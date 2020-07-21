## 获取表单字段

如果不知道创建的表单字段编码是什么，可以通过此接口获取
- - -
#### 版本 ####
v1
- - -
#### SDK方法 ####
FormService.queryFormFields(FormFieldQueryParam formFieldQueryParam)
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
        <td>pkBo</td>
        <td>true</td>
        <td>string</td>
        <td>查看注意事项</td>
    </tr>
</table>

- - - 
#### 请求数据 ####
```
{
	"pkBo": "598df2358ebf4a6ea5394e939378e4be",
}

```
---

#### 返回结果 ####

```
{
	"data": [{
		"errcode": 0,
		"errmsg": "ok",
		"id": "3dabe73c9f894676932dfe45978ea234",
		"url": null,
		"tenantId": "zjhrilpq_approve",
		"revision": 1,
		"status": null,
		"fieldId": "3dabe73c9f894676932dfe45978ea234",
		"variableId": "3dabe73c9f894676932dfe45978ea234",
		"modelId": "8da7b8db-9e46-11ea-9458-9aa2e21290bb",
		"activityId": null,
		"tableFieldName": "f20200525131519KsGAeWTMUi",
		"createTime": "2020-06-01T17:06:01.000+08:00",
		"modifyTime": "2020-06-01T17:06:01.000+08:00",
		"fieldContent": "{\"code\":\"f20200525131519KsGAeWTMUi\",\"binding\":{\"variableId\":\"3dabe73c9f894676932dfe45978ea234\"},\"id\":\"3dabe73c9f894676932dfe45978ea234\"}",
		"variableContent": "{\"name\":\"文本\",\"id\":\"3dabe73c9f894676932dfe45978ea234\",\"type\":{\"name\":\"string\"}}"
	}, {
		"errcode": 0,
		"errmsg": "ok",
		"id": "759a6297431443a7b9c25325d52e683e",
		"url": null,
		"tenantId": "zjhrilpq_approve",
		"revision": 1,
		"status": null,
		"fieldId": "759a6297431443a7b9c25325d52e683e",
		"variableId": "759a6297431443a7b9c25325d52e683e",
		"modelId": "8da7b8db-9e46-11ea-9458-9aa2e21290bb",
		"activityId": null,
		"tableFieldName": "f20200601170558MB4aKfTFTE",
		"createTime": "2020-06-01T17:06:01.000+08:00",
		"modifyTime": "2020-06-01T17:06:01.000+08:00",
		"fieldContent": "{\"code\":\"f20200601170558MB4aKfTFTE\",\"binding\":{\"variableId\":\"759a6297431443a7b9c25325d52e683e\"},\"id\":\"759a6297431443a7b9c25325d52e683e\"}",
		"variableContent": "{\"name\":\"金额\",\"id\":\"759a6297431443a7b9c25325d52e683e\",\"type\":{\"name\":\"number\"}}"
	}],
	"total": 2,
	"start": 0,
	"sort": null,
	"order": null,
	"size": 2,
	"errcode": 0,
	"errmsg": "ok"
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
    <tr align="center">
        <td>fieldId</td>
        <td>String</td>
        <td>可以通过此字段值修改或添加表单数据,</td>
    </tr>
</table>

- - - 

#### 注意事项 ####

- - - 

测试代码中有demo

BillTest.getBillParam()

###### pkbo获取

打开审批流设计器

<div align=center>
<img src="/mybook/cloudapprove/15-/images/1.png"/>
</div>
<p align="center">图 1</p>



