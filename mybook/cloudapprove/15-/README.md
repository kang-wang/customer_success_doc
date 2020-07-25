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
        <td>formData</td>
        <td>true</td>
        <td>list</td>
        <td>表单数据查看注意事项</td>
    </tr>
    <tr align="center">
        <td>subFormMap</td>
        <td>true</td>
        <td>list</td>
        <td>表单子表数据查看注意事项</td>
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


###### 如何获取表单code

<div align=center>
<img src="/mybook/cloudapprove/15-/images/2.png"/>
</div>
<p align="center">图 2</p>

<div align=center>
<img src="/mybook/cloudapprove/15-/images/3.png"/>
</div>
<p align="center">图 3</p>

<div align=center>
<img src="/mybook/cloudapprove/15-/images/4.png"/>
</div>
<p align="center">图 4</p>


###### 如何获取子表的id及枚举的selectid

谷歌浏览器

<div align=center>
<img src="/mybook/cloudapprove/15-/images/5.png"/>
</div>
<p align="center">图 5</p>

<div align=center>
<img src="/mybook/cloudapprove/15-/images/6.png"/>
</div>
<p align="center">图 6</p>

火狐浏览器

<div align=center>
<img src="/mybook/cloudapprove/15-/images/7.png"/>
</div>
<p align="center">图 7</p>

- 子表id:  subFormId
- selectid: selectionId

```
{
	"pk_temp": "38476bff6f2e4923aca4fc1e2dc7ed06",
	"pk_procdef": "iform_5aca65946e:5:3c356a7c-bc3a-11ea-aea0-de2a0f596de1",
	"formBtnVal": {},
	"defaultComment": {},
	"processLauncher": "",
	"form": {
		"title": "云审测试6192",
		"formStyle": {
			"titleFontFamily": "",
			"textAlign": "left"
		},
		"dataPreset": {}
	},
	"cusBtns": [],
	"isMultiBPM": false,
	"isAdvancedFreeFlow": false,
	"formComponents": [
		{
			"layoutDetail": [
				{
					"componentKey": "TdLayout",
	                "layoutDetail": [
						{
							"fieldId": "20200725073118XtkLjzQGxG",
							"title": "选项",
							"optionsType": "Select",
							"options": [
								{
									"name": "选项1",
									"defOption": false,
                                    "selectionId": "20200725073118CGjGSDzKGp"   //枚举值------------------------------
								},
								{
									"name": "选项2",
									"defOption": false,
									"selectionId": "20200725073118aw4djC5He7"
								},
								{
									"name": "选项3",
									"defOption": false,
									"selectionId": "20200725073118yD5POWOnhM"
								}
							]
						}
					],
					"componentKey": "TdLayout",
					"rowSpan": 1,
					"colSpan": 1,
					"coordinate": "3_0"
				}
			]
		},
		{
			"fieldId": "20200725073131rmq32EBZnp",
			"title": "明细子表1",
			"subFormId": "20200725073131t53pTxKWmV",     //子表id------------------------------
			"pk_sub_bo": "42ebb5712cf048beb99fec8977c8a49f",
			"referToSubForm": "",
			"tableName": "iform_zjhrilpq_approve_yscs6192_1",
			"layoutDetail": [
				{
					"fieldId": "20200725073135n2gQMMJSHH",
					"title": "文本3",
					"componentKey": "Text",
					"subFormId": "20200725073131t53pTxKWmV",
					"columncode": "wb3_1595633519225705",
				}
			],
			"colWidthArr": [
				"",
				""
			],
			"emptyRowNotAllowed": false
		}
	],
	"hideProcessAnnex": 0,
	"hideCopyPerson": 0,
	"canSavePDF": true,
	"canWebPrint": true
}
```

###### 表单主表，子表数据赋值

```
/**
     * 保存表单-并发起流程   ----使用编码进行保存
     */
    @Test
    public void saveBillCode() throws RestException {
        IFormSubmitParam parmas = new IFormSubmitParam();
        //TODO:pkbo
        parmas.setPkBo("ab37e4343de142fe9c386fc7fad32ce4");
        List<IFormSubmitData> list = new ArrayList<IFormSubmitData>();
        IFormSubmitData data = new IFormSubmitData();
        //TODO:主表字段code
        data.setCode("wb_159253350464467");
        //TODO:主表字段值
        data.setValue("ccccvbb");
        IFormSubmitData data1 = new IFormSubmitData();
        //TODO:主表字段枚举code
        data1.setCode("xx_1595633519225473");
        //字段值
        //TODO:主表字段枚举值
        data1.setValue("20200725073118aw4djC5He7");
        list.add(data);
        list.add(data1);
        parmas.setFormData(list);
        //---------------------------------------------------------子表数据
        Map<String,List<IFormSubmitParam>> subMap = new HashMap<String,List<IFormSubmitParam>>();
        List<IFormSubmitParam> subDataParamList = new ArrayList<IFormSubmitParam>();
        IFormSubmitParam subParam = new IFormSubmitParam();
        List<IFormSubmitData> subDataList = new ArrayList<IFormSubmitData>();
        subParam.setFormData(subDataList);
        subDataParamList.add(subParam);
        IFormSubmitData subData = new IFormSubmitData();
        //TODO:子表字段CODE
        subData.setCode("wb3_1595633519225705");
        //TODO:子表字段值
        subData.setValue("1111");
        subDataList.add(subData);
        //TODO:key:子表id,value子表数据
        subMap.put("20200725073131t53pTxKWmV",subDataParamList);
        parmas.setSubFormMap(subMap);
        parmas.setStartProcess(true);
        ObjectNode result = (ObjectNode) billService.submitIForm(parmas);
        System.out.println("这是查询表单字段返回的json数据:"+ result.toString());
    }

```

###### 示例DEMO

MyRuntimeTest.saveBillCode()
