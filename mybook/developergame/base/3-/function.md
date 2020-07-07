<h1>函数</h1>

<hr/>

- 前端函数/后端函数/API
- 通过本节课程，可以学习函数的基本操作及调试； 

## 概述

- 在应用下支持开发者自定义根据确定输入信息，基于应用构建平台的脚本引擎，完成自定义逻辑的脚本编写；
- 类型分为前端脚本和后端脚本；
- 前端脚本：可用于控件状态控制、控件赋值、简单数据计算、openAPI调用；
- 后端脚本：可用于后端数据计算、业务调用、数据实体赋值、openAPI调用；
- 函数应用于单据页面、画布页面、流程（工作流、业务流）、表达式、变量、及作为通用函数使用。

## 准备资料

### 实体

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="500px" colspan="4">用户信息</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="4">userinfo</td>
    </tr>
    <tr align="center">
        <td>父实体：</td>
        <td colspan="4"></td>
    </tr>
    <tr align="center">
        <td>引用接口：</td>
        <td colspan="4">自动编码</td>
    </tr>
    <tr align="center">
        <td>属性：</td>
        <td>编码</td>
        <td>名称</td>
        <td>类型</td>
        <td>引用</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>name</td>
        <td>姓名</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>age</td>
        <td>年龄</td>
        <td>整数</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>mobile</td>
        <td>手机号码</td>
        <td>联系方式</td>
        <td></td>
    </tr> 
   <tr align="center">
        <td></td>
        <td>email</td>
        <td>邮箱</td>
        <td>文本</td>
        <td></td>
    </tr> 
   <tr align="center">
        <td></td>
        <td>userid</td>
        <td>用户id</td>
        <td>文本</td>
        <td></td>
    </tr>   
   <tr align="center">
        <td></td>
        <td>startdate</td>
        <td>创建日期</td>
        <td>日期</td>
        <td></td>
    </tr> 
   <tr align="center">
        <td></td>
        <td>enddate</td>
        <td>结束日期</td>
        <td>日期</td>
        <td></td>
    </tr>         
</table>

### 函数

#### 页面初始化->设置默认值（前端函数）

```js
function (event) {
  var viewModel = this;
  function newPseudoGuid () {
        var guid = "";
        for (var i = 1; i <= 32; i++) {
          var n = Math.floor(Math.random() * 16.0).toString(16);
          guid += n;
          if ((i == 8) || (i == 12) || (i == 16) || (i == 20))
            guid += "-";
        }
        return guid;
      }

  var formatDate = function (date) {  
      var y = date.getFullYear();  
      var m = date.getMonth() + 1;  
      m = m < 10 ? '0' + m : m;  
      var d = date.getDate();  
      d = d < 10 ? ('0' + d) : d;  
      return y + '-' + m + '-' + d;  
  }; 
  
  viewModel.get('userid').setValue(newPseudoGuid());
  viewModel.get('startdate').setValue(formatDate(new Date()));
  
} 

```

#### 值改变后事件->校验邮箱格式（前端函数）

```js
function (event) {
  var viewModel = this;
  let email = viewModel.get('email').getValue();
  const validateEmail = str =>
    /^(([^<>()\[\]\.,;:\s@"]+(\.[^<>()\[\]\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/.test(str);
  // validateEmail(mymail@gmail.com) -> true
  if(!validateEmail(email)){
    cb.utils.alert('邮箱格式错误');
  }
} 

```

#### 值改变后事件->校验结束日期（前端函数）

```js
function (event) {
  var viewModel = this;
  var enddate = viewModel.get('enddate').getValue();
  var startdate = viewModel.get('startdate').getValue();
  const isAfterDate = (dateA, dateB) => dateA > dateB;
  if(!isAfterDate(enddate, startdate)) {
    cb.utils.alert('结束日期必须大于开始日期');
  }
}
```

#### 保存前规则->校验手机号和邮箱是否重复（后端函数）

```js
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

```js
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

## 操作流程

1. 新建实体并创建单卡页面
2. 新增函数
3. 在卡片->根层级->页面初始化->添加设置默认值（前端函数）
4. 在卡片->邮箱控件->值改变后事件->添加校验邮箱格式（前端函数）
5. 在卡片->结束日期控件->值改变后事件->添加校验结束日期（前端函数）
6. 在卡片->保存按钮->编辑命令->添加校验手机号和邮箱是否重复（后端函数）
7. 在API发布->新建API->添加根据手机号查询用户信息API（API函数）
8. 函数调试
9. 测试验证