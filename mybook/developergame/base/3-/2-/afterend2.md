<H1>通用后端一</H1>

#### 保存前规则->校验手机号和邮箱是否重复（后端函数）

```
let AbstractTrigger = require('AbstractTrigger');
  class MyTrigger extends AbstractTrigger {
    execute(context,param){
      let data=JSON.parse(param.data);
      let sql = 'select email,mobile,enddate from GT6788AT227.GT6788AT227.user_function_0628 where dr=0';
      let resp = ObjectStore.queryByYonQL(sql);
      var {email,mobile} = data;
      resp.map((v)=>{
        if (email !== null && email===v.email) {
          throw new Error('邮箱已存在！');
        } 
        if (mobile !== null && mobile===v.mobile) {
          throw new Error('手机号已存在！');
        }
      });
     return {};
    }
  }
  exports({"entryPoint":MyTrigger});
```

####  API发布->根据手机号查询用户信息API（API函数）

```
let AbstractAPIHandler = require('AbstractAPIHandler');
  class MyAPIHandler extends AbstractAPIHandler {
   execute(request){
    var mobile = request.mobile;
    var sql='select  code,userid,name,age,mobile,email,tenant_id  from   GT6788AT227.GT6788AT227.user_function_0628  where  mobile like "'+mobile+'"';
    var rst = ObjectStore.queryByYonQL(sql);
    return {"rst":rst,"request":request};
 }
}
exports({"entryPoint":MyAPIHandler});
```