## 功能点：存储阅读记录

### 功能目标

- 进入到【异常记录】卡片页面记录查看信息



### 存储阅读记录知识点

#### 获取当前页面的状态信息

```
//获取当前的单据状态 currentState:  add:新增态，edit:编辑态,browse:浏览态
var currentState = viewModel.getParams().mode;

```

#### 数据加载完成后事件

```
viewModel.on('afterLoadData', function () {
    var id = viewModel.get("id").getValue();
    var body = {
      'id':id,
      'look_situation_m':viewModel.get("look_situation_m").getValue(),
      'look_num':viewModel.get("look_num").getValue()
    }
    cb.rest.invokeFunction("da8c40be08844e46b3d0361ca2e377e9", body,
    function(err, res) {
        //应该是无感的，所以不需要进行处理
    });
}
```

### 记录查看信息功能实现

#### 后端API函数对查看量累加

新建api函数并进入设计器

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/11.png"/>
</div>
<p align="center">图 1</p>

查看阅读记录的单据编码

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/10.png"/>
</div>
<p align="center">图 2</p>

函数代码

```
let AbstractAPIHandler = require('AbstractAPIHandler');
  class MyAPIHandler extends AbstractAPIHandler {
   execute(request){
     var {id,look_situation_m,look_num} = request;
     if(look_num==undefined){look_num=0;}
     //无论是否已经查看都需要改次数   -----------------更新异常记录表的查看次数
     var object = {id:id,look_num:look_num+1};
     var res = ObjectStore.updateById("GT10261AT179.GT10261AT179.abnormalevent",object);
     //获取当前用户的员工信息-------------------------------------------------------------------
     var currentUser = JSON.parse(AppContext()).currentUser;
     var sysId="diwork";
     var tenantId = currentUser.tenantId;
     var userids = [currentUser.id];
     var result = listOrgAndDeptByUserIds(sysId,tenantId,userids);
     var resultJSON = JSON.parse(result);
     if("1"!=resultJSON.status||resultJSON.data==null){
        throw new Error("没有获取到当前用户的组织信息");
     }
     //写入阅读记录表-------------------------------------------------------------------
     var userData = resultJSON.data;
     //需要从数据库中查询出当前人的大区信息、门店信息--TODO:
     var psnid = userData[currentUser.id].id;
     var belongArea ="select '' as id ,id as areaid from GT10261AT179.GT10261AT179.area1 where StaffNew='"+psnid+"'";
     var belongR = ObjectStore.queryByYonQL(belongArea);
     if(undefined==belongR||belongR.length==0){
      var belongStore = "select id,area.id as areaid from GT10261AT179.GT10261AT179.stores1 where StaffNew='"+psnid+"'";
      belongR = ObjectStore.queryByYonQL(belongStore);
     }
     var looklog
     if(belongR.length>0){
      looklog = {StaffNew:psnid,abnormalevent:id,area:belongR[0].areaid,stores:belongR[0].id};
     }else{
      looklog = {StaffNew:psnid,abnormalevent:id};
     }
     //TODO:第三个参数单据编码
     var looklogresult = ObjectStore.insert("GT10261AT179.GT10261AT179.looklog",looklog,"e3e52ae2");
   return {result:true};
 }
}
exports({"entryPoint":MyAPIHandler});

```

#### 前端设置

进入【异常记录】卡片设计器

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/12.png"/>
</div>
<p align="center">图 3</p>

进入页面初始化函数设计器

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/13.png"/>
</div>
<p align="center">图 4</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/14.png"/>
</div>
<p align="center">图 5</p>

```
//页面加载后事件
  viewModel.on('afterLoadData', function () {
    //如果是浏览态--请求api函数添加阅读记录
    if("browse"==currentState){
      var id = viewModel.get("id").getValue();
      var body = {
        'id':id,
        'look_situation_m':viewModel.get("look_situation_m").getValue(),
        'look_num':viewModel.get("look_num").getValue()
      }
      cb.rest.invokeFunction("066c3eebde254465b43ec4662eadaf2c", body,
      function(err, res) {
        //无感，不需要处理
      });
    }
  })
```

### 测试

预览【阅读记录列表】，双击行数据进入卡片页面

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/15.png"/>
</div>
<p align="center">图 6</p>

返回查看阅读次数是否增加

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/16.png"/>
</div>
<p align="center">图 7</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/17.png"/>
</div>
<p align="center">图 8</p>


查看阅读记录是否有数据

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/18.png"/>
</div>
<p align="center">图 9</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/19.png"/>
</div>
<p align="center">图 10</p>








