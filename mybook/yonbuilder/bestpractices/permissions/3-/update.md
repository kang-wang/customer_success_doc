## 查看情况(样式扩展)

### 功能目标

- 根据当前人是否查看异常记录，改变【查看情况】字段的颜色

### 前提准备

使用绑定集团的账号，设置【未查看】为其默认值。为方便修改历史记录，将【查看记录】暂时放出来

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/37.png"/>
</div>
<p align="center">图 1</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/38.png"/>
</div>
<p align="center">图 2</p>

通过点击编码，将历史数据的【查看情况】修改为未查看

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/39.png"/>
</div>
<p align="center">图 3</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/40.png"/>
</div>
<p align="center">图 4</p>

将【异常记录】的未查看隐藏，一般这个字段应该默认不能进行修改

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/37.png"/>
</div>
<p align="center">图 5</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/41.png"/>
</div>
<p align="center">图 6</p>


### 知识点

#### 表格设置数据源后事件

```
let gridModel = viewModel.getGridModel();
gridModel.on('afterSetDataSource', (data) => {
      
      
});

```

#### 操作DOM元素

```
//设置未查看颜色
var selected = document.querySelectorAll("div[title='未查看']");
if(null!=selected){
   selected.forEach((data)=>{
     data.style = data.style.cssText + '; color:red';
   })
}

```

### 功能实现

#### 后端功能实现

新增api函数
<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/43.png"/>
</div>
<p align="center">图 7</p>

后端功能实现

```
let AbstractAPIHandler = require('AbstractAPIHandler');
  class MyAPIHandler extends AbstractAPIHandler {
   execute(request){
      var rows = request.data;
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
      var abnormalevent = [];
      rows.forEach((row)=>{
        abnormalevent.push(row.id);
      })
      var object = abnormalevent.join("','");
      var sql = "select abnormalevent from GT10261AT179.GT10261AT179.looklog where abnormalevent in('"+object+"') and StaffNew='"+userid+"'";
      var res = ObjectStore.queryByYonQL(sql);
      var result = [];
      res.forEach((data)=>{
        result.push(data.abnormalevent);
      })
   return {res:result};
 }
}
exports({"entryPoint":MyAPIHandler});
```

#### 前端功能实现

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/49.png"/>
</div>
<p align="center">图 8</p>

进入【异常记录列表】初始化函数
<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/50.png"/>
</div>
<p align="center">图 9</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/51.png"/>
</div>
<p align="center">图 10</p>


```

let gridModel = viewModel.getGridModel();
gridModel.on('afterSetDataSource', (data) => {
    if(undefined==data||data.length==0)return;
    //获取到表格当前页的数据
    var change_data = JSON.parse(JSON.stringify(data));
    //开启同步块
    var promiseCh = new cb.promise();
    //请求调用后端API函数---【根据页面数据获取当前人的阅读信息】
    cb.rest.invokeFunction("32de814b6db5410fa9d4a197dc7c05bc", {data:change_data},
        function(err, res) {
          if(err!=null){
            cb.utils.alert('获取统计数据异常');
            return false;
          }else{
            var lookResMy = res.res;
            for(j = 0; j < change_data.length; j++) {
              if(lookResMy.indexOf(change_data[j].id)>-1){
                gridModel.setCellValue(j, "look_situation_m", "2");
              }else{
              gridModel.setCellValue(j, "look_situation_m", "1");
              }
            } 
            //设置未查看颜色
            var selected = document.querySelectorAll("div[title='未查看']");
            if(null!=selected){
              selected.forEach((data)=>{
                data.style = data.style.cssText + '; color:red';
              })
            }
          return promiseCh.resolve();
        }
    })
    
  });

```

### 测试

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/52.png"/>
</div>
<p align="center">图 11</p>




















