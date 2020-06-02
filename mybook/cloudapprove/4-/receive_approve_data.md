## 接收监听数据
1. 第三方系统在注册监听事件时填写的回调url，
用来接收监听数据
2. 注意这里的请求，意思是用友系统的请求，返回，是第三方系统的返回
- - -
#### 版本 ####
v1
- - - 
#### 请求方法 ####
POST
- - - 
#### 数据格式 ####
JSON
- - - 
#### 请求参数 ####

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="100px"></td>
        <td width="150px">类型及范围</td>
        <td width="200px">说明</td>
    </tr>
    <tr align="center">
        <td>businessKey</td>
        <td>string</td>
        <td>业务单据号，用来获取表单内容接口会用到</td>
    </tr>
    <tr align="center">
        <td>userCode</td>
        <td>String</td>
        <td>用户 code</td>
    </tr>
    <tr align="center">
        <td>processDefinitionKey</td>
        <td>String</td>
        <td>流程定义 Key</td>
    </tr>
    <tr align="center">
            <td>tenantCode</td>
            <td>String</td>
            <td>租户 code</td>
     </tr>   
</table>

#### 请求数据 ####

```
{
    "thirdPartyUniqueId":"esn2120300",
    "processEnd":true,
    "userPhone":"手机号",
    "canBeArchived":false,
    "language":"zh_CN",
    "source":"ESN",
    "tenantCode":"approve_zjhrilpq",
    "userName":"姓名",
    "userId":"c4cf4330-86e2-4d89-9b4d-cea1bf3369eb",
    "userCode":"HRC18211102015",
    "processDefinitionKey":"iform_3e41d17055",
    "businessKey":"7cf6b90bf9a24bb6abe53de22ee73227:bea0303d91b94f91bb71169ec431b5b5",
    "userMail":"邮箱",
    "tenantId":"zjhrilpq_approve",
    "processInstId":"961127d8-a47f-11ea-9c8c-66700af9a2c9",
    "yht_access_token":"bttKzg1RjhBeFNsZ0piRG1qcWJERkh3Umt5N1hxOWRBQU00dmNqR2RyWnl4ME9vTGpjd0JPNXRPMVk1Sys5MWNBWmpXYTA2V3VnUkZVNGpFOFhxVHdDajdNYURZL2I0clFIT3N4VSsyQlJ0WGFUelRKQTNZQ1gzYWtpZkZiei8yT2lfX2V1Yy55b255b3VjbG91ZC5jb20.__4c1c33f0f2a10c21a9bbce7bf4c7dcf3_1590998301780"
}

```

- - - 

#### 返回结果 ####

第三方服务返回结果

```
成功： {"desc":"OK","msgSuccess":true} 
失败：{"desc":"扣预算失败!","msgSuccess":false}

```

#### 注意事项 ####

测试代码中有demo 

ListenController.approveContent()
