# 函数操作实体API

## 新增

#### 保存实体

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">方法：</td>
        <td width="500px" colspan="2">insert(URI,object,billNum)</td>
    </tr>
    <tr align="center">
        <td>描述：</td>
        <td colspan="2">保存实体，默认自动生成主键、审计信息</td>
    </tr>
    <tr align="center">
        <td>入参：</td>
        <td colspan="2"></td>
    </tr>
    <tr align="center">
        <td>名称</td>
        <td>含义</td>
        <td>示例</td>
    </tr>
    <tr align="center">
        <td>URI</td>
        <td>实体统一资源标识符</td>
        <td>developplatform.AX000888.PX012991</td>
    </tr>
    <tr align="center">
        <td>object</td>
        <td>实体对象，支持包含子实体，包含子实体时基于主子表关系值</td>
        <td>{name:"qqq",bustype:"1639837036187904",item41d:"45gty",isWfControlled:"1",verifystate:"0",returncount:"0",pX000008_tabpane0List:[{hasDefaultInit:true,item20l:"www"},{hasDefaultInit:true,item20l:"mmm"}]}</td>
    </tr>
    <tr align="center">
        <td>billNum</td>
        <td>表单编码</td>
        <td>f6f7e02c</td>
    </tr>
    <tr align="center">
        <td>返回值：</td>
        <td colspan="2">该实体对象</td>
    </tr>  
</table>

###### 示例

```
var object = {name:"qqq",bustype:"1639837036187904",item41d:"45gty",isWfControlled:"1",verifystate:"0",returncount:"0",pX000008_tabpane0List:[{hasDefaultInit:true,item20l:"www"},{hasDefaultInit:true,item20l:"mmm"}]};
var res = ObjectStore.insert("developplatform.AX000003.PX000008",object,'f6f7e02c');  
```

```
//JavaScript对象的JSON串示例
{
        "name":"qqq",
        "bustype":"1639837036187904",
        "item41d":"45gty",
        "isWfControlled":true,
        "verifystate":0,
        "returncount":0,
        "pX000008_tabpane0List":[
            {
                "hasDefaultInit":true,
                "item20l":"www",
                "id":"20bdd921c3234673a04d3219d5129021",
                "meta_fk":"fdccf0cd1a7b472fa0db47c66632bc79",
                "pubts":"Mar 13, 2020 5:04:26 PM"
            },
            {
                "hasDefaultInit":true,
                "item20l":"mmm",
                "id":"eef6430c6bac4b2892d019a80a2cf5a1",
                "meta_fk":"fdccf0cd1a7b472fa0db47c66632bc79",
                "pubts":"Mar 13, 2020 5:04:26 PM"
            }
        ],
        "id":"fdccf0cd1a7b472fa0db47c66632bc79",
        "creator":"xxx",
        "creationtime":"Mar 13, 2020 5:04:31 PM",
        "modifier":"xxx",
        "modifiedtime":"Mar 13, 2020 5:04:31 PM",
        "pubts":"Mar 13, 2020 5:04:31 PM"
 }
```

- - - 

###### Base62解密

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">方法：</td>
        <td width="500px" colspan="2">Base62Decode(data)</td>
    </tr>
    <tr align="center">
        <td>描述：</td>
        <td colspan="2">对Base62加密后的字符串进行Base62解密</td>
    </tr>
    <tr align="center">
        <td>入参：</td>
        <td colspan="2"></td>
    </tr>
    <tr align="center">
        <td>名称</td>
        <td>含义</td>
        <td>示例</td>
    </tr>
    <tr align="center">
        <td>data</td>
        <td>待解密的字符串</td>
        <td>"cGFzc3dvcmQ"</td>
    </tr>
    <tr align="center">
        <td>返回值：</td>
        <td colspan="2">解密后的字符串</td>
    </tr>  
</table>

###### 示例

```
var data ="cGFzc3dvcmQ";
var res =Base62Decode(data);

//password
```

- - - 

#### Base64
###### Base64加密

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">方法：</td>
        <td width="500px" colspan="2">Base64Encode(data)</td>
    </tr>
    <tr align="center">
        <td>描述：</td>
        <td colspan="2">对字符串进行Base64加密</td>
    </tr>
    <tr align="center">
        <td>入参：</td>
        <td colspan="2"></td>
    </tr>
    <tr align="center">
        <td>名称</td>
        <td>含义</td>
        <td>示例</td>
    </tr>
    <tr align="center">
        <td>data</td>
        <td>待加密的字符串</td>
        <td>"password"</td>
    </tr>
    <tr align="center">
        <td>返回值：</td>
        <td colspan="2">加密后的字符串</td>
    </tr>  
</table>

###### 示例

```
var data ="password";
var res =Base64Encode(data);

//cGFzc3dvcmQ=
```

- - - 

###### Base64解密

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">方法：</td>
        <td width="500px" colspan="2">Base64Decode(data)</td>
    </tr>
    <tr align="center">
        <td>描述：</td>
        <td colspan="2">对Base64加密后的字符串进行Base64解密</td>
    </tr>
    <tr align="center">
        <td>入参：</td>
        <td colspan="2"></td>
    </tr>
    <tr align="center">
        <td>名称</td>
        <td>含义</td>
        <td>示例</td>
    </tr>
    <tr align="center">
        <td>data</td>
        <td>待解密的字符串</td>
        <td>"cGFzc3dvcmQ="</td>
    </tr>
    <tr align="center">
        <td>返回值：</td>
        <td colspan="2">解密后的字符串</td>
    </tr>  
</table>

###### 示例

```
var data ="cGFzc3dvcmQ=";
var res =Base64Decode(data);

//password
```

- - - 

#### HEX
###### HEX编码

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">方法：</td>
        <td width="500px" colspan="2">HEXEncode(data)</td>
    </tr>
    <tr align="center">
        <td>描述：</td>
        <td colspan="2">对字符串进行HEX编码</td>
    </tr>
    <tr align="center">
        <td>入参：</td>
        <td colspan="2"></td>
    </tr>
    <tr align="center">
        <td>名称</td>
        <td>含义</td>
        <td>示例</td>
    </tr>
    <tr align="center">
        <td>data</td>
        <td>待加密的字符串</td>
        <td>"password"</td>
    </tr>
    <tr align="center">
        <td>返回值：</td>
        <td colspan="2">编码后的字符串</td>
    </tr>  
</table>

###### 示例

```
var data ="password";
var res =HEXEncode(data);

//70617373776f7264
```

- - - 

###### HEX解码

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">方法：</td>
        <td width="500px" colspan="2">HEXDecode(data)</td>
    </tr>
    <tr align="center">
        <td>描述：</td>
        <td colspan="2">对字符串进行HEX解码</td>
    </tr>
    <tr align="center">
        <td>入参：</td>
        <td colspan="2"></td>
    </tr>
    <tr align="center">
        <td>名称</td>
        <td>含义</td>
        <td>示例</td>
    </tr>
    <tr align="center">
        <td>data</td>
        <td>待解码的字符串</td>
        <td>"70617373776f7264"</td>
    </tr>
    <tr align="center">
        <td>返回值：</td>
        <td colspan="2">解码后的字符串</td>
    </tr>  
</table>

###### 示例

```
var data ="70617373776f7264";
var res =HEXDecode(data);

//password
```

- - - 

#### Jwt
###### Jwt token获取

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">方法：</td>
        <td width="500px" colspan="2">JwtCreate(userId,userName,subject)</td>
    </tr>
    <tr align="center">
        <td>入参：</td>
        <td colspan="2"></td>
    </tr>
    <tr align="center">
        <td>名称</td>
        <td>含义</td>
        <td>示例</td>
    </tr>
    <tr align="center">
        <td>userId</td>
        <td>用户ID</td>
        <td>"12345"</td>
    </tr>
    <tr align="center">
        <td>userName</td>
        <td>用户名</td>
        <td>"wangbo"</td>
    </tr>
    <tr align="center">
        <td>subject</td>
        <td>主题</td>
        <td>"测试"</td>
    </tr>
    <tr align="center">
        <td>返回值：</td>
        <td colspan="2">token</td>
    </tr>  
</table>

###### 示例

```
var res = JwtCreate("12345","wangbo","测试");

//eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiLmtYvor5UiLCJ1c2VyTmFtZSI6IndhbmdibyIsImV4cCI6MTU1NjE3NjYwNiwidXNlcklkIjoiMTIzNDUiLCJpYXQiOjE1NTYxNzY2MDF9.FNVh-NbFHgScsbbuwLvQL-sOqLuaAoI8jxMvudq81J8
```

- - -

###### Jwt token解析

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">方法：</td>
        <td width="500px" colspan="2">JwtDecode(token)</td>
    </tr>
    <tr align="center">
        <td>描述：</td>
        <td colspan="2">对Jwt token进行解析</td>
    </tr>
    <tr align="center">
        <td>入参：</td>
        <td colspan="2"></td>
    </tr>
    <tr align="center">
        <td>名称</td>
        <td>含义</td>
        <td>示例</td>
    </tr>
    <tr align="center">
        <td>token</td>
        <td>待解析的token</td>
        <td>"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiLmtYvor5UiLCJ1c2VyTmFtZSI6IndhbmdibyIsImV4cCI6MTU1NjE3NjYwNiwidXNlcklkIjoiMTIzNDUiLCJpYXQiOjE1NTYxNzY2MDF9.FNVh-NbFHgScsbbuwLvQL-sOqLuaAoI8jxMvudq81J8"</td>
    </tr>
    <tr align="center">
        <td>返回值：</td>
        <td colspan="2">解码获得的信息</td>
    </tr>  
</table>

###### 示例

```
var data ="eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiLmtYvor5UiLCJ1c2VyTmFtZSI6IndhbmdibyIsImV4cCI6MTU1NjE3NjYwNiwidXNlcklkIjoiMTIzNDUiLCJpYXQiOjE1NTYxNzY2MDF9.FNVh-NbFHgScsbbuwLvQL-sOqLuaAoI8jxMvudq81J8";
var res =JwtDecode(data);
```

```
{
    "parts": [
        "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9",
        "eyJzdWIiOiLmtYvor5UiLCJ1c2VyTmFtZSI6IndhbmdibyIsImV4cCI6MTU1NjE3NjYwNiwidXNlcklkIjoiMTIzNDUiLCJpYXQiOjE1NTYxNzY2MDF9",
        "FNVh-NbFHgScsbbuwLvQL-sOqLuaAoI8jxMvudq81J8"
    ],
    "header": {
        "algorithm": "HS256",
        "type": "JWT",
        "tree": {
            "alg": {
                "_value": "HS256"
            },
            "typ": {
                "_value": "JWT"
            }
        }
    },
    "payload": {
        "subject": "测试",
        "expiresAt": "Apr 25, 2019 3:16:46 PM",
        "issuedAt": "Apr 25, 2019 3:16:41 PM",
        "tree": {
            "sub": {
                "_value": "测试"
            },
            "userName": {
                "_value": "wangbo"
            },
            "exp": {
                "_value": 1556176606
            },
            "userId": {
                "_value": "12345"
            },
            "iat": {
                "_value": 1556176601
            }
        }
    }
}
```

- - - 

#### 获取当前登录用户上下文

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">方法：</td>
        <td width="500px" colspan="2">AppContext()</td>
    </tr>
</table>

###### 示例

```
var res = AppContext();
```
```
{
  "currentUser": {
    "id": "07f90f73-24b0-41fa-83b2-8108d99cb98e",
    "name": "测试",
    "tenantId": "gb0ucj8l"
  }
}
```