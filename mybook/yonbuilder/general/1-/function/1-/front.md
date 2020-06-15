# 前端函数

## 简单卡片界面

取值赋值

```
function (event) {
  var viewModel = this;
  var container = viewModel.getGridModels()[0];
  var age  = viewModel.get("age").getValue();  //取值
  viewModel.get("age").setValue("34567");   //赋值
  cb.utils.alert(age);
}

```

修改值后函数

```
function (event) {
  var viewModel = this;
  viewModel.get('age').on('afterValueChange', function(params) {
      cb.utils.alert(params.value);
            
  });
} 

```

值改变前事件

```
function (event) {
  var viewModel = this;
  viewModel.get('age').on('beforeValueChange', function(params) {
      cb.utils.alert(params.value);
            
  });
} 

```


