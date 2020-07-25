<H1>前端函数调用后端函数</H1>


## 后端函数示例

```
let AbstractAPIHandler = require('AbstractAPIHandler');

class MyAPIHandler extends AbstractAPIHandler {

  execute(request){
    var r = request.r;
    return {apidata: 3*r};
  }
}
exports({"entryPoint":MyAPIHandler});

```

## 前端函数示例

cb.rest.invokeFunction("后端函数id","传参","回调处理")

```
function (event) {

  var viewModel = this;

  cb.rest.invokeFunction("7f4237efde03414aaf80b8aa4b5e8ef8", {r:2},

  function(err, res) {

    console.log(err);

    console.log(res);

  });

}
```

#### 后端函数id怎么获取？

<div align=center>
<img src="/mybook/developergame/base/3-/4-/images/1.png"/>
</div>
<p align="center">图 1</p>

<div align=center>
<img src="/mybook/developergame/base/3-/4-/images/2.png"/>
</div>
<p align="center">图 2</p>

