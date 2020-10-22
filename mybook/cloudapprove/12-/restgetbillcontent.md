## 根据条件获取表单数据
根据条件获取表单数据
- - -
#### URL ####
https://ys.yonyoucloud.com/ubpm-web-rest/service/query/ext/iformData

- - - 
#### 支持格式 ####
JSON
- - - 
#### HTTP请求方式 ####
POST
- - - 
#### HEADER参数 ####

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="200px">Content-Type</td>
        <td width="300px">application/json;charset=UTF-8</td>
    </tr>
    <tr align="center">
        <td>restservice</td>
        <td>REST_SERVICE_1.0.0</td>
    </tr>
    <tr align="center">
        <td>cache-control</td>
        <td>no-cache</td>
    </tr>
    <tr align="center">
        <td>source</td>
        <td>approve</td>
    </tr>
    <tr align="center">
        <td>tenant</td>
        <td>租户id,请看注意事项</td>
    </tr>
    <tr align="center">
        <td>securitytenant</td>
        <td>租户id,请看注意事项</td>
    </tr>
    <tr align="center">
        <td>sign</td>
        <td>认证字符串--后端加密算法生成的,根据请求token+url+tenant，具体获取请看注意事项</td>
    </tr>
</table>

#### 请求参数 ####
- - - 

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="100px"></td>
        <td width="100px">必选</td>
        <td width="150px">类型及范围</td>
        <td width="200px">说明</td>
    </tr>
    <tr align="center">
        <td>pkbo</td>
        <td>true</td>
        <td>String</td>
        <td></td>
    </tr>
    <tr align="center">
        <td>columnCode</td>
        <td>false</td>
        <td>string</td>
        <td>字段编码</td>
    </tr>
    <tr align="center">
            <td>columnValue</td>
            <td>false</td>
            <td>string</td>
            <td>字段值</td>
        </tr>
</table>

- - - 
#### 请求JSON数据 ####
```
{
	"pkBo": "6f3edadfda924146a18fe9357dca60f9",
	"queryOperator": "And",
	"size": 1000,
	"sqlConditions": [
		{
			"columnCode": "rq_160307198384328",
			"columnValue": "2020-10-18",
			"queryOperator": "Equal"
		}
	],
	"start": 0
}
```
---

#### 返回结果 ####

```
{
	"data": [
		{
			"wb1_1603071983843105": "33",
			"wb3_160307198384359": "33",
			"wb2_1603071983843779": "44",
			"createuser": "0f059088-9c92-4769-a3e7-8f1a341cc3df",
			"rq_160307198384328": "2020-10-18",
			"version": 1,
			"pk_boins": "16c420b831e94ab68689e7e65910c80b",
			"dr": 0,
			"pk_procdef": "processKey:1:cffb83ab-5d13-11ea-84d3-f676d4a6f6aa",
			"pk_procdefins": "218c28e6-11ad-11eb-8b9a-36730f7bdd3f",
			"pk_temp": "b4774eb51ac1484a9a10bd7207be4cdc",
			"sysversion": 0,
			"startdept": "1641272788504832",
			"startorg": "1640198360125696",
			"status": "end",
			"ts": "2020-10-19 09:48:05"
		}
	],
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

#### 注意事项 ####

- 获取租户id:

<div align=center>
<img src="/mybook/cloudapprove/2-/images/1.png"/>
</div>
<p align="center">图 1</p>

- 获取sign

[获取sign](/mybook/cloudapprove/12-/restsign.md) 