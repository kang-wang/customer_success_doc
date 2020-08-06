# 常用函数

## 自定义CSS样式

注意用友业务系统的UI/UE需要保持一致，不要使用个性化的样式

```
function (event) {
  var viewModel = this;
  var style = document.createElement('style');
  style.type = 'text/css';
  document.head.appendChild(style);
  style.sheet.insertRule(".u-button {color:#6495ed;}", 0);
}
```

## 加载自定义JS

注意用友业务系统的交互需要保持一致，不要使用个性化的交互

```
function (event) {
  var viewModel = this;
  extscripturls.push('http://resources.yonyoucloud.com/packages/TestExternal.js');
}
```