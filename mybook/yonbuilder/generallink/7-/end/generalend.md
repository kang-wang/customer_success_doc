# 常用后端函数

## 日志

```javascript

console.log('Enter into getList function');
console.log('Function name: {}, params: {}','getList','tenantId');
console.debug('Enter into getList function');
console.debug('Function name: {}, params: {}','getList','tenantId');
console.warn('Enter into getList function');
console.warn('Function name: {}, params: {}','getList','tenantId');
console.error('Enter into getList function');
console.error('Function name: {}, params: {}','getList','tenantId');

```
查看输出的日志

<div align=center>
<img src="/mybook/yonbuilder/generallink/7-/end/images/1.png"/>
</div>
<p align="center">图 1</p>


## 更改保存数据

```javascript
//后端函数绑定到规则链
let AbstractTrigger = require('AbstractTrigger');
  class MyTrigger extends AbstractTrigger {
    execute(context,param){
      //可以回写修改new1的值
      param.data[0].set('new1','22');
     return {};
    }
  }
exports({"entryPoint":MyTrigger});
```





