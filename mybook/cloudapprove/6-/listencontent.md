## 查询租户下注册的监听列表
查询租户下注册的监听列表

- - -
#### 版本 ####
v1
- - -
#### SDK方法 ####
DefaultIdentityService.queryBasicdatas(BasicdataQueryParam params)
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
        <td>tenantId</td>
        <td>true</td>
        <td>string</td>
        <td>租户id</td>
    </tr>
</table>

- - - 
#### 请求数据 ####
```
{
	"id": null,
	"name": null,
	"code": null,
	"tenantId": "zjhrilpq",
	"type": null,
	"source": null,
	"category": null,
	"procDefId": null,
	"activityId": null
}
```
---

#### 返回结果 ####

```
{
	"data": [{
		"id": "d0021362-5d13-11ea-84d3-f676d4a6f6aa",
		"multiLevelControlId": null,
		"tenantId": "zjhrilpq_approve",
		"revision": 1,
		"createTime": 1583215026000,
		"modifyTime": 1583215026000,
		"lanCode": null,
		"code": "form_relation_process_listener",
		"name": "表单关系推送事件监听",
		"type": "process_listener",
		"enable": false,
		"url": "https://ys.yonyoucloud.com/form-relation/pushItem/push",
		"token": "form_relation_fake_token",
		"operations": null,
		"source": "ESN",
		"category": null,
		"procDefId": null,
		"activityId": null,
		"sync": true,
		"revisionNext": 2
	}, {
		"id": "d0021363-5d13-11ea-84d3-f676d4a6f6aa",
		"multiLevelControlId": null,
		"tenantId": "zjhrilpq_approve",
		"revision": 1,
		"createTime": 1583215026000,
		"modifyTime": 1583215026000,
		"lanCode": null,
		"code": "form_relation_process_activity_listener",
		"name": "表单关系推送事件监听",
		"type": "process_activity_listener",
		"enable": false,
		"url": "https://ys.yonyoucloud.com/form-relation/pushItem/push",
		"token": "form_relation_fake_token",
		"operations": null,
		"source": "ESN",
		"category": null,
		"procDefId": null,
		"activityId": null,
		"sync": true,
		"revisionNext": 2
	}, {
		"id": "d0021364-5d13-11ea-84d3-f676d4a6f6aa",
		"multiLevelControlId": null,
		"tenantId": "zjhrilpq_approve",
		"revision": 1,
		"createTime": 1583215026000,
		"modifyTime": 1583215026000,
		"lanCode": null,
		"code": "form_relation_process_start_listener",
		"name": "表单关系推送事件监听",
		"type": "process_start_listener",
		"enable": false,
		"url": "https://ys.yonyoucloud.com/form-relation/pushItem/push",
		"token": "form_relation_fake_token",
		"operations": null,
		"source": "ESN",
		"category": null,
		"procDefId": null,
		"activityId": null,
		"sync": true,
		"revisionNext": 2
	}, {
		"id": "815c264b-6f2e-11ea-a838-76932bec7e85",
		"multiLevelControlId": null,
		"tenantId": "zjhrilpq_approve",
		"revision": 1,
		"createTime": 1585205612000,
		"modifyTime": 1585205611000,
		"lanCode": null,
		"code": "businessCreate_listener",
		"name": "业务扩展平台",
		"type": "process_listener",
		"enable": true,
		"url": "https://ys.yonyoucloud.com/business-expansion-platform/rest/datacenter/BPMCallback",
		"token": "BEP",
		"operations": null,
		"source": "ESN",
		"category": null,
		"procDefId": null,
		"activityId": null,
		"sync": true,
		"revisionNext": 2
	}, {
		"id": "8161084c-6f2e-11ea-a838-76932bec7e85",
		"multiLevelControlId": null,
		"tenantId": "zjhrilpq_approve",
		"revision": 1,
		"createTime": 1585205612000,
		"modifyTime": 1585205611000,
		"lanCode": null,
		"code": "businessCreate_listener",
		"name": "业务扩展平台",
		"type": "process_listener",
		"enable": true,
		"url": "https://ys.yonyoucloud.com/business-expansion-platform/rest/datacenter/BPMCallback",
		"token": "BEP",
		"operations": null,
		"source": "BEP",
		"category": null,
		"procDefId": null,
		"activityId": null,
		"sync": true,
		"revisionNext": 2
	}, {
		"id": "8166fbbd-6f2e-11ea-a838-76932bec7e85",
		"multiLevelControlId": null,
		"tenantId": "zjhrilpq_approve",
		"revision": 1,
		"createTime": 1585205612000,
		"modifyTime": 1585205611000,
		"lanCode": null,
		"code": "BEP",
		"name": "业务扩展平台",
		"type": "process_start_listener",
		"enable": true,
		"url": "https://ys.yonyoucloud.com/business-expansion-platform/rest/datacenter/BPMCallback",
		"token": "BEP",
		"operations": null,
		"source": "BEP",
		"category": null,
		"procDefId": null,
		"activityId": null,
		"sync": true,
		"revisionNext": 2
	}, {
		"id": "74826347-9f30-11ea-951c-da57d7039e8a",
		"multiLevelControlId": null,
		"tenantId": "zjhrilpq_approve",
		"revision": 1,
		"createTime": 1590484105000,
		"modifyTime": 1590484105000,
		"lanCode": null,
		"code": "haikang",
		"name": "海康门卫监听",
		"type": "process_listener",
		"enable": true,
		"url": "http://310l2268a8.wicp.vip/approve/listen",
		"token": "dsfdfgagfdgfdaewvdg",
		"operations": null,
		"source": "ESN",
		"category": null,
		"procDefId": "iform_3e41d17055",
		"activityId": null,
		"sync": true,
		"revisionNext": 2
	}],
	"total": 7,
	"start": 0,
	"sort": null,
	"order": null,
	"size": 7,
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
</table>

- - - 

#### 注意事项 ####

- - - 

测试代码中有获取表单内容的demo

ApproveListenTest.getListen()



