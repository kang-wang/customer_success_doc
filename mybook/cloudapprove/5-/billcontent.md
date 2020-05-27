## 获取表单内容
触发监听事件后，返回给第三方的并不是表单内容，里面包含了
参数有四个businessKey（业务单据号），
userCode（用户code），
processDefinitionKey（流程定义Key），
tenantCode（租户code）
可以根据businessKey获取表单内容
- - -
#### 版本 ####
v1
- - -
#### SDK方法 ####
FormService.queryIFormData(IFormDataQueryParam param)
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
        <td>pkBoins</td>
        <td>true</td>
        <td>String</td>
        <td>查看注意事项</td>
    </tr>
</table>

- - - 
#### 请求数据 ####
```
{
	"pkBo": "598df2358ebf4a6ea5394e939378e4be",
	"pkBoins": "754ba83feac74e0cb6eaadda5451f654",
	"queryOperator": "And",
	"size": 1000,
	"start": 0
}
```
---

#### 返回结果 ####

```
{
	"data": [{
		"ceshi_1590379312039108": "dfsfsfsfsdfs",
		"modifyuser": "0f059088-9c92-4769-a3e7-8f1a341cc3df",
		"createuser": "0f059088-9c92-4769-a3e7-8f1a341cc3df",
		"version": 2,
		"pk_boins": "754ba83feac74e0cb6eaadda5451f654",
		"dr": 0,
		"wb_159013329575110": "1233456",
		"pk_procdef": "iform_ffaddda7b6:1:a57b2c77-9bff-11ea-b2cd-9e4f8041e636",
		"modifydate": "2020-05-25 12:03:58",
		"pk_procdefins": "7f9c7e07-9e3c-11ea-b2cd-9e4f8041e636",
		"pk_temp": "b0fce2cb86874afaa3c46a4950185453",
		"sysversion": 0,
		"startdept": "1641272788504832",
		"startorg": "1640198360125696",
		"status": "end",
		"ts": "2020-05-25 12:02:06"
	}],
	"total": 1,
	"start": 0,
	"sort": null,
	"order": null,
	"size": 1000,
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
        <td>data</td>
        <td>array</td>
        <td>返回的具体字段，由您的表单内容决定</td>
    </tr>
</table>

- - - 

#### 注意事项 ####

- - - 

测试代码中有获取表单内容的demo

ApproveListenTest.getBillContent()


###### pkBo和pkBoins如何获取

```
通过businessKey拆分可以获得

public Object getBillContent(String businessKey) throws RestException {
        IFormDataQueryParam param =new IFormDataQueryParam();
        String[] pks = businessKey.split(":");
        param.setPkBo(pks[1]);
        param.setPkBoins(pks[0]);
        BpmRest bpmRest = BpmRests.getBpmRest(getBaseParam());
        FormService formService = bpmRest.getFormService();
        Object obj=formService.queryIFormData(param);
        return obj;
}

```



