# 函数

前端扩展/后端扩展/API/

#### 概述

通过本节课程，可以学习函数的基本操作及调试

#### 准备资料

###### 页面初始化

```
function (event) {
  var viewModel = this;
  var container = viewModel.getGridModels()[0];
  var age  = viewModel.get("age").getValue();  //取值
  viewModel.get("age").setValue("34567");   //赋值
  cb.utils.alert(age);
}

```

###### 值改变后事件

```
function (event) {
  var viewModel = this;
  viewModel.get('age').on('afterValueChange', function(params) {
      cb.utils.alert(params.value);
            
  });
} 

```

###### 后端函数

```

let AbstractTrigger = require('AbstractTrigger');
  class MyTrigger extends AbstractTrigger {
    execute(context,param){
      var data=JSON.parse(param.data);
      if (data!==null && data.age!==null) {
        var age= data.age;
        if(age<18){
          throw new Error('年龄必须大于18岁');
        }
      }  
     return {};
    }
  }
  exports({"entryPoint":MyTrigger});

```

###### API

```
let AbstractAPIHandler = require('AbstractAPIHandler');
  class MyAPIHandler extends AbstractAPIHandler {
   execute(request){
    var billid = request.id;
    var sql='select  materialName as mt,id,zjl,cgje,cgsl,xh,gysxx,org_id,cgdj  from   AX001705.AX001705.cgddzb420   where  cgddzb420Fk="'+billid+'"';
    var rst = ObjectStore.queryByYonQL(sql);
    return {"rst":rst,"request":request};
 }
}
exports({"entryPoint":MyAPIHandler});

```