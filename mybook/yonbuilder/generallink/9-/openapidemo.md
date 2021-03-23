### 封装公用获取token

创建一个api函数，让其他api函数引用

[临时获取开放平台token方案](mybook/yonbuilder/generallink/9-/tempopenapi.md)

<div align=center>
<img src="/mybook/yonbuilder/generallink/9-/images/1.png"/>
</div>
<p align="center">图 1</p>

<div align=center>
<img src="/mybook/yonbuilder/generallink/9-/images/2.png"/>
</div>
<p align="center">图 2</p>

### GET方式调用开放平台接口

```
let AbstractAPIHandler = require('AbstractAPIHandler');
  class MyAPIHandler extends AbstractAPIHandler {
   execute(request){
    //使用公共函数--------------begin
    let func1 = extrequire("GT14087AT2.backDefaultGroup.getOpenApiToken");
    let res = func1.execute(request);
    //使用公共函数--------------end
    var token = res.access_token;
    var deptId = request;
    var requrl = "https://api.diwork.com/yonbip/digitalModel/admindept/detail?access_token="+token+"&id="+deptId;
    var strResponse = postman("GET", requrl,null);
    var responseObj = JSON.parse(strResponse);
    var deptDetail;
    if("200"==responseObj.code){
      deptDetail = responseObj.data;
    }
   return {res:deptDetail};
 }
}
exports({"entryPoint":MyAPIHandler});

```

### POST方式调用开放平台接口

```
let AbstractAPIHandler = require('AbstractAPIHandler');
  class MyAPIHandler extends AbstractAPIHandler {
   execute(request){
      let base_path = "https://api.diwork.com/yonbip/digitalModel/staff/list";
      var hmd_contenttype = "application/json;charset=UTF-8";  
      let header = {
      'Content-Type':hmd_contenttype
      };
      var body={
        "pageIndex": "1",
        "pageSize": "10"
      };
      let func1 = extrequire("GT14087AT2.backDefaultGroup.getOpenApiToken");
      let res = func1.execute(request);
      var token = res.access_token;
    //请求数据
      let apiResponse = postman("post", base_path.concat("?access_token="+token),JSON.stringify(header),JSON.stringify(body));
   return {apiResponse};
 }
}
exports({"entryPoint":MyAPIHandler});
```


### 界面如果使用公共函数

<div align=center>
<img src="/mybook/yonbuilder/generallink/9-/images/3.png"/>
</div>
<p align="center">图 3</p>

<div align=center>
<img src="/mybook/yonbuilder/generallink/9-/images/4.png"/>
</div>
<p align="center">图 4</p>