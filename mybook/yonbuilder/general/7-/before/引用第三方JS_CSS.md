# 引用第三方JS/CSS



<a name="25fb6452"></a>
# 加载自定义JS（方式一）


```javascript
function (event) {
  var viewModel = this;
  extscripturls.push('http://resources.yonyoucloud.com/packages/TestExternal.js');
}
```


<a name="aeb249fc"></a>
# 加载自定义JS/CSS(JavaScript方式)


```javascript
function (event) {
  var viewModel = this;
  //加载css文件
  function loadCssFile(params){
    var fileref=document.createElement("link")
    fileref.rel="stylesheet";
    fileref.type="text/css";
    fileref.href=params;
    fileref.media="screen";
    var headobj=document.getElementsByTagName('head')[0];
    headobj.appendChild(fileref);
  }
  //加载自定义样式
  function loadStyle(params){
    var headobj=document.getElementsByTagName('head')[0];
    var style = document.createElement('style');
    style.type = 'text/css';
    headobj.appendChild(style);
    style.sheet.insertRule(params, 0);
  }
  //加载js
  function loadjs(params){
    var headobj=document.getElementsByTagName('head')[0];
    var script = document.createElement("script");
    script.type = "text/javascript";
    script.src = params;
    headobj.appendChild(script);
  }
  //加载css样式
  loadCssFile("https://a.amap.com/jsapi_demos/static/demo-center/css/demo-center.css");
  //加载js
  loadjs("https://webapi.amap.com/maps?v=1.4.15&key=9b2f6b9f4b37bfe98e4e48cb2a70c376&plugin=AMap.Autocomplete");
//加载样式
  loadStyle(".mycircle {border-radius: 50%;width: 60px;height: 60px;background: #5A5AAD; text-align:center}");
}
```
