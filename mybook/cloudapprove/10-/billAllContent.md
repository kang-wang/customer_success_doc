## 获取表单全部内容
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
}
```
---

#### 返回结果 ####

```
{
	"data":[
            {
                "modifyuser":"0f059088-9c92-4769-a3e7-8f1a341cc3df",
                "createuser":"0f059088-9c92-4769-a3e7-8f1a341cc3df",
                "version":1,
                "pk_boins":"1c3886745874457c8a76c91663963019",
                "dr":0,
                "wb_159013329575110":"234567",
                "pk_procdef":"iform_ffaddda7b6:1:a57b2c77-9bff-11ea-b2cd-9e4f8041e636",
                "modifydate":"2020-05-25 11:04:52",
                "pk_procdefins":"6caaeafa-9e34-11ea-b2cd-9e4f8041e636",
                "pk_temp":"0120d81120464dec8f169015c4b51378",
                "sysversion":0,
                "startdept":"1641272788504832",
                "startorg":"1640198360125696",
                "status":"end",
                "ts":"2020-05-25 11:04:18"
            },
            {
                "modifyuser":"0f059088-9c92-4769-a3e7-8f1a341cc3df",
                "createuser":"0f059088-9c92-4769-a3e7-8f1a341cc3df",
                "version":1,
                "pk_boins":"202ee903d60a44ae90c485a17875f52a",
                "dr":0,
                "wb_159013329575110":"2334566",
                "pk_procdef":"iform_ffaddda7b6:1:a57b2c77-9bff-11ea-b2cd-9e4f8041e636",
                "modifydate":"2020-05-22 15:45:32",
                "pk_procdefins":"2e09841e-9c00-11ea-9458-9aa2e21290bb",
                "pk_temp":"0120d81120464dec8f169015c4b51378",
                "sysversion":0,
                "startdept":"1641272788504832",
                "startorg":"1640198360125696",
                "status":"end",
                "ts":"2020-05-22 15:45:17"
            },
            {
                "modifyuser":"0f059088-9c92-4769-a3e7-8f1a341cc3df",
                "createuser":"0f059088-9c92-4769-a3e7-8f1a341cc3df",
                "version":1,
                "pk_boins":"6e2966b651064c71be7306287195ee95",
                "dr":0,
                "wb_159013329575110":"dffghjkl",
                "pk_procdef":"iform_ffaddda7b6:1:a57b2c77-9bff-11ea-b2cd-9e4f8041e636",
                "modifydate":"2020-05-25 11:13:38",
                "pk_procdefins":"b13b24f8-9e35-11ea-951c-da57d7039e8a",
                "pk_temp":"0120d81120464dec8f169015c4b51378",
                "sysversion":0,
                "startdept":"1641272788504832",
                "startorg":"1640198360125696",
                "status":"end",
                "ts":"2020-05-25 11:13:22"
            },
            {
                "ceshi_1590379312039108":"dfsfsfsfsdfs",
                "modifyuser":"0f059088-9c92-4769-a3e7-8f1a341cc3df",
                "createuser":"0f059088-9c92-4769-a3e7-8f1a341cc3df",
                "version":2,
                "pk_boins":"754ba83feac74e0cb6eaadda5451f654",
                "dr":0,
                "wb_159013329575110":"1233456",
                "pk_procdef":"iform_ffaddda7b6:1:a57b2c77-9bff-11ea-b2cd-9e4f8041e636",
                "modifydate":"2020-05-25 12:03:58",
                "pk_procdefins":"7f9c7e07-9e3c-11ea-b2cd-9e4f8041e636",
                "pk_temp":"b0fce2cb86874afaa3c46a4950185453",
                "sysversion":0,
                "startdept":"1641272788504832",
                "startorg":"1640198360125696",
                "status":"end",
                "ts":"2020-05-25 12:02:06"
            },
            {
                "ceshi_1590379312039108":"1111",
                "modifyuser":"0f059088-9c92-4769-a3e7-8f1a341cc3df",
                "createuser":"0f059088-9c92-4769-a3e7-8f1a341cc3df",
                "version":2,
                "pk_boins":"8187d6577ff84d40801236e0cad12289",
                "dr":0,
                "wb_159013329575110":"12345",
                "pk_procdef":"iform_ffaddda7b6:1:a57b2c77-9bff-11ea-b2cd-9e4f8041e636",
                "modifydate":"2020-05-26 16:58:03",
                "pk_procdefins":"f95d8932-9f2e-11ea-b2cd-9e4f8041e636",
                "pk_temp":"b0fce2cb86874afaa3c46a4950185453",
                "sysversion":0,
                "startdept":"1641272788504832",
                "startorg":"1640198360125696",
                "status":"end",
                "ts":"2020-05-26 16:57:48"
            },
            {
                "modifyuser":"0f059088-9c92-476-a3e7-8f1a341cc3df",
                "createuser":"0f059088-9c92-479-a3e7-8f1a341cc3df",
                "version":1,
                "pk_boins":"af38903a917f498db6d39873b189bc5",
                "dr":0,
                "wb_159013329575110":"12232443",
                "pk_procdef":"iform_ffaddda7b6:1:a57b2c77-9bff-11ea-b2cd-9e4f8041e636",
                "modifydate":"2020-05-25 10:51:47",
                "pk_procdefins":"95a2d012-9e32-11ea-9458-9aa2e21290bb",
                "pk_temp":"0120d81120464dec8f19015c4b51378",
                "sysversion":0,
                "startdept":"164127278504832",
                "startorg":"164019836025696",
                "status":"end",
                "ts":"2020-05-25 10:51:08"
            },
            {
                "ceshi_159037931203108":"ssss",
                "modifyuser":"0f059088-9c92-4769-a3e7-8f1a341cc3df",
                "createuser":"0f059088-9c92-476-a3e7-8f1a341cc3df",
                "version":2,
                "pk_boins":"b0eb7dcbd89246eb93ea9f0e71f6317",
                "dr":0,
                "wb_159013329575110":"sss",
                "pk_procdef":"iform_ffaddda7b6:1:a57b2c77-9bff-11ea-b2cd-9e4f8041e636",
                "modifydate":"2020-05-26 17:10:02",
                "pk_procdefins":"a79ca9e9-9f30-11ea-951c-da57d7039e8a",
                "pk_temp":"b0fce2cb86874afaa3c46a450185453",
                "sysversion":0,
                "startdept":"1641272788504832",
                "startorg":"1640198360125696",
                "status":"end",
                "ts":"2020-05-26 17:09:50"
            },
            {
                "modifyuser":"0f059088-9c92-4769-a3e7-8f1a341cc3df",
                "createuser":"0f059088-9c92-4769-a3e7-8f1a341cc3df",
                "version":1,
                "pk_boins":"bf3a506ee1214b319a0c95f58da34b7",
                "dr":0,
                "wb_159013329575110":"11111",
                "pk_procdef":"iform_ffaddda7b6:1:a57b2c77-9bff-11ea-b2cd-9e4f8041e636",
                "modifydate":"2020-05-25 10:08:55",
                "pk_procdefins":"a3f5dcb8-9e2c-11ea-b2cd-9e4f8041e636",
                "pk_temp":"0120d81120464dec8f1690154b51378",
                "sysversion":0,
                "startdept":"1641272788504832",
                "startorg":"1640198360125696",
                "status":"end",
                "ts":"2020-05-25 10:08:35"
            },
            {
                "modifyuser":"0f059088-9c92-4769-a3e7-8f1a341cc3df",
                "createuser":"0f059088-9c92-4769-a3e7-f1a341cc3df",
                "version":1,
                "pk_boins":"d3d6cbf48e944f39ab0924887375c2de",
                "dr":0,
                "wb_159013329575110":"234567sss",
                "pk_procdef":"iform_ffaddda7b6:1:a57b2c77-9ff-11ea-b2cd-9e4f8041e636",
                "modifydate":"2020-05-25 11:07:31",
                "pk_procdefins":"d6f01eee-9e34-11ea-9458-9aa2e21290bb",
                "pk_temp":"0120d8112064dec8f169015c4b51378",
                "sysversion":0,
                "startdept":"164127278854832",
                "startorg":"164019836025696",
                "status":"end",
                "ts":"2020-05-25 11:07:16"
            }
        ],
        "total":9,
        "start":0,
        "sort":null,
        "order":null,
        "size":1000,
        "errcode":0,
        "errmsg":"ok"
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