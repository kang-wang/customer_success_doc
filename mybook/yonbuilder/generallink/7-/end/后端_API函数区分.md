# 后端/API函数区分

<a name="8wmlt"></a>
### 后端函数应用场景
- 后端函数主要用于标准版预制按钮功能的扩展开发（规则链）
<a name="7qNEG"></a>
### API函数应用场景

- 前端函数可调用API函数，实现在标准版下前端调后端的能力
- 发布为接口，供其他服务商调用

# 示例

## 后端函数示例

### 保存前规则->校验手机号和邮箱是否重复（后端函数）

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

## API函数示例

###  根据手机号查询用户信息API

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

