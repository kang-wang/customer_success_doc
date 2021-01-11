## 公共函数使用

有些公共的前端函数，需要进行复用，可以参考此文档


### 新建公共函数

<div align=center>
<img src="/mybook/yonbuilder/generallink/7-/before/images/8.png"/>
</div>
<p align="center">图 1</p>

<div align=center>
<img src="/mybook/yonbuilder/generallink/7-/before/images/9.png"/>
</div>
<p align="center">图 2</p>

<div align=center>
<img src="/mybook/yonbuilder/generallink/7-/before/images/10.png"/>
</div>
<p align="center">图 3</p>

```
cb.defineInner([],function() {
  var MyExternal = {  
    testMethod: function (params) {
      console.log(params);
    }
  }
   return MyExternal;
})
```


### 使用公共函数

根据自己的业务需求，创建并绑定函数

<div align=center>
<img src="/mybook/yonbuilder/generallink/7-/before/images/11.png"/>
</div>
<p align="center">图 4</p>

<div align=center>
<img src="/mybook/yonbuilder/generallink/7-/before/images/12.png"/>
</div>
<p align="center">图 5</p>

```
function (event) {
  var viewModel = this;
  cb.requireInner(["/opencomponentsystem/public/GT12074AT404/generalfun"], function(a) {
      a.testMethod(23456);
  })
}

```

