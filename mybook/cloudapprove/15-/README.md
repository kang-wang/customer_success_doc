## 提交表单并发起流程
- - -
#### 版本 ####
v1
- - -
#### SDK方法 ####
FormService.submitIForm(IFormSubmitParam param)
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
    <tr align="center">
        <td>List</td>
        <td>true</td>
        <td>list</td>
        <td>查看注意事项</td>
    </tr>
</table>

- - - 
#### 请求数据 ####
```
{
	"formData": [
		{
			"code": "20200619102500w9gu9KrDrK",
			"value": "ccccvbb"
		}
	],
	"pkBo": "ab37e4343de142fe9c386fc7fad32ce4",
	"startProcess": true,
	"supplySaveData": true
}
```
---

#### 返回结果 ####

```
{
	"errcode": 0,
	"errmsg": "ok",
	"id": "f9a62b91caf011ea8f57d2df464dbf42",
	"url": null,
	"tenantId": null,
	"revision": 0,
	"status": null,
	"tableName": null,
	"formKey": null,
	"tableFieldValue": null
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


#### 注意事项 ####

###### 示例demo

```
//示例demo
MyRuntimeTest.saveBill();

```

###### pkbo获取

打开审批流设计器

<div align=center>
<img src="/mybook/cloudapprove/15-/images/1.png"/>
</div>
<p align="center">图 1</p>

###### 传参list

```
List<IFormSubmitData> list = new ArrayList<IFormSubmitData>();
IFormSubmitData data = new IFormSubmitData();
//获取表单字段返回的tableFieldName去除前缀f
data.setFieldId("20200619102500w9gu9KrDrK");
//字段值
data.setValue("ccccvbb");
list.add(data);
parmas.setFormData(list);

```
