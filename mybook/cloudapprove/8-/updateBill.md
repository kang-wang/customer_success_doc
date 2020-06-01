## 更新表单数据

获取表单内上传的文件
- - -
#### 版本 ####
v1
- - -
#### SDK方法 ####
FormService.updateBill(IFormSubmitParam param)
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
    <tr align="center">
        <td>formData</td>
        <td>false</td>
        <td>List</td>
        <td>查看注意事项</td>
    </tr> 
    <tr align="center">
            <td>subFormMap</td>
            <td>false</td>
            <td>Map</td>
            <td>查看注意事项</td>
        </tr>   
</table>

- - - 
#### 请求数据 ####
```
{
	"pkBo": "598df2358ebf4a6ea5394e939378e4be",
	"pkBoins": "754ba83feac74e0cb6eaadda5451f654",
	"fromData": [{
		"name": 11
	}],
	"subFormMap": {
		"iform_1234": [{
			"name": 1
		}, {
			"name": 2
		}]
	}
}

```
---

#### 返回结果 ####

```
{
	"errcode": 0,
	"errmsg": "updated",
	"id": null,
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

- - - 

#### 注意事项 ####

- - - 

测试代码中有demo

BillTest.updateParam()


###### pkBo和pkBoins如何获取

```
通过businessKey拆分可以获得

public IFormDataQueryParam getPkBoAndBoins(String businessKey){
        IFormDataQueryParam param =new IFormDataQueryParam();
        String[] pks = businessKey.split(":");
        param.setPkBo(pks[1]);
        param.setPkBoins(pks[0]);
        return param;
}

fromData和subFormMap根据表单字段编码赋值即可

```



