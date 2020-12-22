## 数据权限

### 功能目标

- 集团负责人可以查看所有的数据信息
- 大区负责人可以查看大区内所有门店的异常数据信息
- 门店负责人只能看到自己门店内发生的异常数据信息
- "员工状态"类事项不做权限控制，全平台都可以查看

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/2-/images/1.png"/>
</div>
<p align="center">图 1</p>


### 权限过滤知识点

#### 列表界面查询前事件-（自定义过滤条件-简单条件查询）

```
viewModel.on('beforeSearch',function(args){
    args.isExtend = true;
    var commonVOs = args.params.condition.commonVOs;  //通用检查查询条件
    commonVOs.push({
        itemName:'id',
        op:'eq',
        value1:''
    });
    commonVOs.push({
        itemName:'id',
        op:'in',
        value1:['1'.'2']
    });
})

```


条件| 说明
---|---
itemName | 查询区字段控件编码
op | 比较符号，具体支持请查看查询区字段控件【比较符】属性，不同控制支持比较符不同
value1|传值



#### 列表界面查询前事件-（自定义过滤条件-复杂条件查询）

```

viewModel.on('beforeSearch',function(args){
    args.isExtend = true;
    var conditions = args.params.condition;
    conditions.simpleVOs=
        [{
            "logicOp": "and",
            "conditions": [{
                "logicOp": "or",
                "conditions": [{
                    "field": "matter_type_m",
                    "op": "eq",
                    "value1": '3'
                    },
                    {
                    "field": "StaffNew",
                    "op": "in",
                    "value1": permissions
                }]
            }]
        }];
})

```

条件| 说明
---|---
logicOp|and/or
conditions|条件存储key
field | 查询区字段控件编码
op | 比较符号，具体支持请查看查询区字段控件【比较符】属性，不同控制支持比较符不同
value1|传值


#### 同步函数

```
function(event){
    //自己的代码逻辑比如请求后台等相关比较耗时的操作，需要页面渲染和请求是同步执行而不是异步操作的情况
    var promise = new cb.promise(); //--第一步声明需要同步
    cb.rest.invokeFunction("2abae82cef154bd194d7069135011395", {},
      function(err, res) {
        promise.resolve();  //--第二步：执行完自己的逻辑后，释放同步
      });
}

```


函数 | 说明
---|---
promise | 同步函数
invokeFunction | 请求API函数方法


#### 按钮显示控制

```
//TODO：button11qi  -----按钮编码
viewModel.get("button11qi").setVisible(false);  //设置按钮不显示
viewModel.get("button11qi").setVisible(true);  //设置按钮显示

```


#### 后端API函数获取当前登录用户员工信息

```

let AbstractAPIHandler = require('AbstractAPIHandler');
  class MyAPIHandler extends AbstractAPIHandler {
   execute(request){
     //获取当前用户的身份信息-----------
     var currentUser = JSON.parse(AppContext()).currentUser;  //通过上下文获取当前的用户信息
     var sysId="diwork";
     var tenantId = currentUser.tenantId;
     var userids = [currentUser.id];
     var result = listOrgAndDeptByUserIds(sysId,tenantId,userids); //获取当前用户的组织和部门信息
     var resultJSON = JSON.parse(result);
     var userid;
     if("1"==resultJSON.status&&resultJSON.data!=null){
       //根据当前用户信息去查询员工表
       var userData = resultJSON.data;
       //业务系统员工id
       userid = userData[currentUser.id].id; //员工id
     }else{
       throw new Error("获取员工信息异常");
     }
   return {res:userid};
 }
}
exports({"entryPoint":MyAPIHandler});

```

### 【异常记录列表】权限过滤 功能实现

#### 后端API函数----权限过滤

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/2-/images/5.png"/>
</div>
<p align="center">图 2</p>

权限过滤后端函数

```

let AbstractAPIHandler = require('AbstractAPIHandler');
  class MyAPIHandler extends AbstractAPIHandler {
   execute(request){
     //获取当前用户的身份信息-----------
     var currentUser = JSON.parse(AppContext()).currentUser;
     var sysId="diwork";
     var tenantId = currentUser.tenantId;
     var userids = [currentUser.id];
     var result = listOrgAndDeptByUserIds(sysId,tenantId,userids);
     var resultJSON = JSON.parse(result);
     var userid;
     var allData;
     if("1"==resultJSON.status&&resultJSON.data!=null){
       //根据当前用户信息去查询员工表
       var userData = resultJSON.data;
       //业务系统员工id
       userid = userData[currentUser.id].id;
     }else{
       throw new Error("获取员工信息异常");
     }
     //先判断是否是集团的人员
     var orgsql = "select StaffNew from GT10261AT179.GT10261AT179.org1 where StaffNew='"+userid+"'";
     var orgres = ObjectStore.queryByYonQL(orgsql);
     if(orgres.length>0){
       allData="all";
     }else{
       //判断是否为管理人员 -----一个大区的区长默认为是有下属门店的，根据门店来获取区长信息 
     var managerSql = "select StaffNew, id, area.StaffNew as areapsn,area.id as areaid from GT10261AT179.GT10261AT179.stores1 where "
     +" StaffNew='"+userid+"' or area.StaffNew ='"+userid+"'";
     var res = ObjectStore.queryByYonQL(managerSql);
     //权限范围内的异常创建人，根据人来筛选
     var result = [];
     if(res.length>0){
       //说明是管理人员   --默认身份互斥
       res.forEach((data)=>{
         if(userid==data.areapsn){
           //说明是区长
           result.push(data.StaffNew);
         }
       })
       //加入自身
       result.push(userid);
     }
     }
   return {res:result,allData:allData};
 }
}
exports({"entryPoint":MyAPIHandler});

```

#### 新增前端扩展函数----列表查询过滤

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/2-/images/2.png"/>
</div>
<p align="center">图 3</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/2-/images/4.png"/>
</div>
<p align="center">图 4</p>

获取API函数id

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/2-/images/10.png"/>
</div>
<p align="center">图 5</p>

列表查询过滤前端函数

```

function(event){
    let gridModel = viewModel.getGridModel();
    var commonVOs,reqCondition,permissions,alldata;
    viewModel.on('beforeSearch',function(args){
      //需要获取当前人的身份信息，确定默认的查询条件
      var promise = new cb.promise();
      setTimeout(function() {
        //TODO: API函数id
        cb.rest.invokeFunction("a85ffbc6110146fc8fc5af7c546bbec5", {},
      function(err, res) {
        if(err!=null){
          cb.utils.alert('查询数据异常');
          permissions = [];
          return false;
        }else{
          permissions = res.res;
          alldata = res.allData;
          //如果是员工不允许新增单据
          if(undefined==permissions||permissions.length==0){
            //将新增按钮隐藏btnAdd为按钮编码
            viewModel.get("btnAdd").setVisible(false);
          }
          args.isExtend = true;
          //请求数据的条件，获取统计信息的时候需要用到
          reqCondition= args.params.condition;
          commonVOs = args.params.condition.commonVOs;
          if(undefined==permissions){
            //设置一个不可能查询出数据的条件
            cb.utils.alert('查询数据异常--获取人员失败');
              commonVOs.push({
                itemName:'id',
                op:'eq',
                value1:''
              });
          }else{
            if(undefined==alldata){
              if(permissions.length>0){
                var conditions = args.params.condition;
                conditions.simpleVOs=
                  [{
                    "logicOp": "and",
                    "conditions": [{
                        "logicOp": "or",
                        "conditions": [{
                          "field": "matter_type_m",   //设置事项类型为员工状态
                          "op": "eq",
                          "value1": '3'
                          },
                          {
                          "field": "StaffNew",    //人员权限信息
                          "op": "in",
                          "value1": permissions
                        }]
                  }]
                }];
            }else{
              commonVOs.push({
                itemName:'matter_type_m',  //设置事项类型为员工状态
                op:'eq',
                value1:'3'
              });
            }
          }
        }
        promise.resolve();
        }
      })
      }, 10);
      return promise;
  })
}

```

### 【异常记录】卡片设置默认创建人 功能实现

#### 调整【异常记录】卡片布局样式

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/2-/images/12.png"/>
</div>
<p align="center">图 6</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/2-/images/6.png"/>
</div>
<p align="center">图 7</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/2-/images/7.png"/>
</div>
<p align="center">图 8</p>


<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/2-/images/8.png"/>
</div>
<p align="center">图 9</p>

设置创建人不可编辑
<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/2-/images/15.png"/>
</div>
<p align="center">图 10</p>

#### 后端API函数----获取当前用户的员工id

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/2-/images/11.png"/>
</div>
<p align="center">图 11</p>

API函数：获取当前用户的员工信息

```
let AbstractAPIHandler = require('AbstractAPIHandler');
  class MyAPIHandler extends AbstractAPIHandler {
   execute(request){
     var currentUser = JSON.parse(AppContext()).currentUser;
     var sysId="diwork";
     var tenantId = currentUser.tenantId;
     var userids = [currentUser.id];
     var result = listOrgAndDeptByUserIds(sysId,tenantId,userids);
     var resultJSON = JSON.parse(result);
     var userid;
     var username;
     if("1"==resultJSON.status&&resultJSON.data!=null){
       //根据当前用户信息去查询员工表
       var userData = resultJSON.data;
       //业务系统员工id
       userid = userData[currentUser.id].id;
       username = userData[currentUser.id].name;
     }else{
       throw new Error("获取员工信息异常");
     }
   return {userid:userid,username:username};
 }
}
exports({"entryPoint":MyAPIHandler});

```

#### 新增前端扩展函数

设置创建人不可编辑

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/2-/images/12.png"/>
</div>
<p align="center">图 12</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/2-/images/13.png"/>
</div>
<p align="center">图 13</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/2-/images/14.png"/>
</div>
<p align="center">图 14</p>

设置创建人默认值为当前用户

```
function (event) {
  var viewModel = this;
  //获取当前页面的单据状态
  var currentState = viewModel.getParams().mode;
  if("add"==currentState){    //add:新增态，edit:编辑态, browse:浏览态
    //需要请求后台设置当前创建者的默认值
    //TODO: api函数id
    cb.rest.invokeFunction("7e0dbb242a98483181c2ef91e041c2d8", {},
    function(err, res) {
      if(err!=null){
        cb.utils.alert('设置默认创建者异常');
      }else{
        //设置默认值
        viewModel.get("StaffNew_name").setValue(res.username);
        viewModel.get("StaffNew").setValue(res.userid);
      }
    })
  }
}
```


### 验证

#### 填充数据


范围 | 二级范围| 异常标题
---|---|---
大区一 | |大区一异常
| 门店一|门店一异常
大区二 | |大区二异常
集团||员工状态类异常

#### 效果展示

集团页面预览效果

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/2-/images/16.png"/>
</div>
<p align="center">图 15</p>

大区一预览效果

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/2-/images/17.png"/>
</div>
<p align="center">图 16</p>

大区二预览效果

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/2-/images/18.png"/>
</div>
<p align="center">图 17</p>


门店一预览效果

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/2-/images/19.png"/>
</div>
<p align="center">图 18</p>
