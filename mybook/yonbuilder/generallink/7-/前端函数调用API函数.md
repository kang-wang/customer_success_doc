# 前端函数调用API函数



<a name="3dbf0c11"></a>
# 应用场景

<br />简单的前端调后台，实现增删查改操作<br />

<a name="348b9936"></a>
# API函数示例


```javascript
let AbstractAPIHandler = require('AbstractAPIHandler');

class MyAPIHandler extends AbstractAPIHandler {

  execute(request){
    var r = request.r;
    return {apidata: 3*r};
  }
}
exports({"entryPoint":MyAPIHandler});
```


<a name="e1c53fef"></a>
# 前端函数示例


```javascript
function (event) {

  var viewModel = this;
	//cb.rest.invokeFunction("后端函数id","传参","回调处理")
  cb.rest.invokeFunction("7f4237efde03414aaf80b8aa4b5e8ef8", {r:2},

  function(err, res) {

    console.log(err);

    console.log(res);

  });

}
```


<a name="2256ed19"></a>
## 后端函数id怎么获取？

<div align=center>
<img src="/mybook/yonbuilder/generallink/7-/images/1.jpeg"/>
</div>
<p align="center">图 1</p>

<div align=center>
<img src="/mybook/yonbuilder/generallink/7-/images/2.jpeg"/>
</div>
<p align="center">图 2</p>