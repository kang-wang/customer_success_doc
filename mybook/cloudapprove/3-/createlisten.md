## 审批事件监听注册
如果想在审批流的某个环节，调用第三方的接口，处理某些操作。可以
使用此接口注册审批监听
- - -
#### 版本 ####
v1
- - -
#### SDK方法 ####
DefaultIdentityService的insertBasicData(BasicDataResourceParam basicDataResouceParam)方法

- - - 
#### 请求参数 ####

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="100px"></td>
        <td width="100px">必选</td>
        <td width="150px">类型及范围</td>
        <td width="200px">说明</td>
    </tr>
    <tr align="center">
        <td>code</td>
        <td>true</td>
        <td>string</td>
        <td>监听编码-自定义：字母数字组合</td>
    </tr>
    <tr align="center">
        <td>name</td>
        <td>true</td>
        <td>String</td>
        <td>监听名称</td>
    </tr>
    <tr align="center">
            <td>type</td>
            <td>true</td>
            <td>String</td>
            <td>监听类型，具体选值，请看注意事项</td>
    </tr>
    <tr align="center">
        <td>tenantId</td>
        <td>true</td>
        <td>String</td>
        <td>租户id</td>
    </tr>
    <tr align="center">
        <td>source</td>
        <td>true</td>
        <td>String</td>
        <td>请看注意事项</td>
    </tr>
    <tr align="center">
        <td>url</td>
        <td>true</td>
        <td>String</td>
        <td>访问第三方的url</td>
    </tr>    
    <tr align="center">
        <td>token</td>
        <td>true</td>
        <td>String</td>
        <td>访问第三方的密钥(安全性)，没有可随便写，但必输</td>
    </tr>
    <tr align="center">
        <td>procDefId</td>
        <td>true</td>
        <td>String</td>
        <td>请查看注意事项</td>
    </tr>            
</table>

- - - 
#### 请求数据 ####
```
{
	"id": null,
	"code": "haiang",
	"name": "门卫监听",
	"createTime": null,
	"modifyTime": null,
	"enable": true,
	"tenantId": "zjhri",
	"type": "process_listener",
	"token": "dsfdfgagfdgfdaewvdg",
	"url": "http://310l28.p.vip/approve/listen",
	"operations": null,
	"source": "ESN",
	"category": null,
	"procDefId": "iform_3e41d17055",
	"activityId": null
}
```
---

#### 返回结果 ####

```
{
	"errcode": 0,
	"errmsg": "ok",
	"id": null,
	"url": "http://310l28.p.vip/approve/listen",
	"tenantId": "zjhri",
	"revision": 0,
	"status": null,
	"code": "haikang",
	"name": "门卫监听",
	"parent": null,
	"token": "dsfdfgagfdgfdaewvdg",
	"operations": null,
	"category": null,
	"sync": true
}

```
- - - 
#### 返回字段说明 ####

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="100px">返回值字段</td>
        <td width="80px">字段类型</td>
        <td width="200px">字段说明</td>
    </tr>
    <tr align="center">
        <td>errcode</td>
        <td>int</td>
        <td>0:Success</td>
    </tr>
    <tr align="center">
        <td>errmsg</td>
        <td>string</td>
        <td>描述</td>
    </tr>
</table>

- - - 

#### 注意事项 ####

测试代码中有注册云审——协同的审批监听的demo
ApproveListenTest.testListen()
- - - 

###### type取值范围

描述|选值
---|---
流程结束监听|process_listener
流程开始监听|process_start_listener
环节结束监听|process_activity_listener
流程开始监听|process_start_listener
消息回调|message_send
外部参与人|user
模型创建回调|model_save_listener
服务任务回调|service_callback


###### 获取source&&procDefId

登录业务系统，打开自己创建的审批流的流程设计器
按F12打开浏览器控制台

<div align=center>
<img src="/mybook/cloudapprove/3-/images/1.png"/>
</div>
<p align="center">图 1</p>

获取procDefId
processDefinionId由两个冒号隔开，去第一个冒号前的字符串即可
eg:  12345:67:890
procDefId = 12345

<div align=center>
<img src="/mybook/cloudapprove/3-/images/2.png"/>
</div>
<p align="center">图 2</p>

获取source

<div align=center>
<img src="/mybook/cloudapprove/3-/images/2.png"/>
</div>
<p align="center">图 3</p>


