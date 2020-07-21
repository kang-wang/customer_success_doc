# 函数操作实体API

## 新增

### 保存实体

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">方法：</td>
        <td width="500px" colspan="2">insert(URI,object,billNum)</td>
    </tr>
    <tr align="center">
        <td>描述：</td>
        <td colspan="2">保存实体，默认自动生成主键、审计信息</td>
    </tr>
    <tr align="center">
        <td>入参：</td>
        <td colspan="2"></td>
    </tr>
    <tr align="center">
        <td>名称</td>
        <td>含义</td>
        <td>示例</td>
    </tr>
    <tr align="center">
        <td>URI</td>
        <td>实体统一资源标识符</td>
        <td>developplatform.AX000888.PX012991</td>
    </tr>
    <tr align="center">
        <td>object</td>
        <td>实体对象，支持包含子实体，包含子实体时基于主子表关系值</td>
        <td>{name:"qqq",bustype:"1639837036187904",item41d:"45gty",isWfControlled:"1",verifystate:"0",returncount:"0",
        pX000008_tabpane0List:[{hasDefaultInit:true,item20l:"www"},{hasDefaultInit:true,item20l:"mmm"}]}</td>
    </tr>
    <tr align="center">
        <td>billNum</td>
        <td>表单编码</td>
        <td>f6f7e02c</td>
    </tr>
    <tr align="center">
        <td>返回值：</td>
        <td colspan="2">该实体对象</td>
    </tr>  
</table>

#### 示例

```
var object = {name:"qqq",bustype:"1639837036187904",item41d:"45gty",isWfControlled:"1",
verifystate:"0",returncount:"0",pX000008_tabpane0List:[{hasDefaultInit:true,item20l:"www"},
{hasDefaultInit:true,item20l:"mmm"}]};
var res = ObjectStore.insert("developplatform.AX000003.PX000008",object,'f6f7e02c');  
```

```
//JavaScript对象的JSON串示例
{
        "name":"qqq",
        "bustype":"1639837036187904",
        "item41d":"45gty",
        "isWfControlled":true,
        "verifystate":0,
        "returncount":0,
        "pX000008_tabpane0List":[
            {
                "hasDefaultInit":true,
                "item20l":"www",
                "id":"20bdd921c3234673a04d3219d5129021",
                "meta_fk":"fdccf0cd1a7b472fa0db47c66632bc79",
                "pubts":"Mar 13, 2020 5:04:26 PM"
            },
            {
                "hasDefaultInit":true,
                "item20l":"mmm",
                "id":"eef6430c6bac4b2892d019a80a2cf5a1",
                "meta_fk":"fdccf0cd1a7b472fa0db47c66632bc79",
                "pubts":"Mar 13, 2020 5:04:26 PM"
            }
        ],
        "id":"fdccf0cd1a7b472fa0db47c66632bc79",
        "creator":"xxx",
        "creationtime":"Mar 13, 2020 5:04:31 PM",
        "modifier":"xxx",
        "modifiedtime":"Mar 13, 2020 5:04:31 PM",
        "pubts":"Mar 13, 2020 5:04:31 PM"
 }
```

- - - 

### 批量插入

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">方法：</td>
        <td width="500px" colspan="2">insertBatch(URI,objectList,billNum)</td>
    </tr>
    <tr align="center">
        <td>描述：</td>
        <td colspan="2">批量保存实体，默认自动生成审计信息</td>
    </tr>
    <tr align="center">
        <td>入参：</td>
        <td colspan="2"></td>
    </tr>
    <tr align="center">
        <td>名称</td>
        <td>含义</td>
        <td>示例</td>
    </tr>
    <tr align="center">
        <td>URI</td>
        <td>实体统一资源标识符</td>
        <td>developplatform.AX000888.PX012991</td>
    </tr>
    <tr align="center">
        <td>objectList</td>
        <td>实体对象列表，支持包含子实体，包含子实体时基于主子表关系值</td>
        <td>[{name:"qqq",bustype:"1639837036187904",item41d:"45gty",isWfControlled:"1",verifystate:"0",returncount:"0",
        pX000008_tabpane0List:[{hasDefaultInit:true,item20l:"www"},{hasDefaultInit:true,item20l:"mmm"}]},
        {name:"www",bustype:"1639837036187904",item41d:"45gty",isWfControlled:"1",verifystate:"0",returncount:"0",
        pX000008_tabpane0List:[{hasDefaultInit:true,item20l:"rrr"},{hasDefaultInit:true,item20l:"ttt"}]}];</td>
    </tr>
    <tr align="center">
        <td>billNum</td>
        <td>表单编码</td>
        <td>f6f7e02c</td>
    </tr>
    <tr align="center">
        <td>返回值：</td>
        <td colspan="2">新增的多个实体对象</td>
    </tr>  
</table>

#### 示例

```
var objectList = [{name:"qqq",bustype:"1639837036187904",item41d:"45gty",isWfControlled:"1",
verifystate:"0",returncount:"0",pX000008_tabpane0List:[{hasDefaultInit:true,item20l:"www"},
{hasDefaultInit:true,item20l:"mmm"}]},{name:"www",bustype:"1639837036187904",item41d:"45gty",isWfControlled:"1",
verifystate:"0",returncount:"0",pX000008_tabpane0List:[{hasDefaultInit:true,item20l:"rrr"},{hasDefaultInit:true,item20l:"ttt"}]}];
var res = ObjectStore.insertBatch("developplatform.AX000003.PX000008",objectList,'f6f7e02c'); 
```
```
//JavaScript对象的JSON串示例
[
        {
            "name":"qqq",
            "bustype":"1639837036187904",
            "item41d":"45gty",
            "isWfControlled":true,
            "verifystate":0,
            "returncount":0,
            "pX000008_tabpane0List":[
                {
                    "hasDefaultInit":true,
                    "item20l":"www",
                    "id":"8f900a6d08dc4d44b506f05dc74dc865",
                    "meta_fk":"0cddce5165194dddbb16bf75566e8667",
                    "pubts":"Mar 13, 2020 5:49:15 PM"
                },
                {
                    "hasDefaultInit":true,
                    "item20l":"mmm",
                    "id":"f4857dc2f70c4ab285119a88fce3ac4b",
                    "meta_fk":"0cddce5165194dddbb16bf75566e8667",
                    "pubts":"Mar 13, 2020 5:49:15 PM"
                }
            ],
            "id":"0cddce5165194dddbb16bf75566e8667",
            "creator":"xxx",
            "creationtime":"Mar 13, 2020 5:49:20 PM",
            "modifier":"xxx",
            "modifiedtime":"Mar 13, 2020 5:49:20 PM",
            "pubts":"Mar 13, 2020 5:49:21 PM"
        },
        {
            "name":"www",
            "bustype":"1639837036187904",
            "item41d":"45gty",
            "isWfControlled":true,
            "verifystate":0,
            "returncount":0,
            "pX000008_tabpane0List":[
                {
                    "hasDefaultInit":true,
                    "item20l":"rrr",
                    "id":"7eeaecc36344454395469157f0414654",
                    "meta_fk":"1227ee93a5564f2e8c3b228e67b076c7",
                    "pubts":"Mar 13, 2020 5:49:33 PM"
                },
                {
                    "hasDefaultInit":true,
                    "item20l":"ttt",
                    "id":"cc784d51fcf042f0a26e02c8e3a4c2b4",
                    "meta_fk":"1227ee93a5564f2e8c3b228e67b076c7",
                    "pubts":"Mar 13, 2020 5:49:33 PM"
                }
            ],
            "id":"1227ee93a5564f2e8c3b228e67b076c7",
            "creator":"xxx",
            "creationtime":"Mar 13, 2020 5:49:38 PM",
            "modifier":"xxx",
            "modifiedtime":"Mar 13, 2020 5:49:38 PM",
            "pubts":"Mar 13, 2020 5:49:38 PM"
        }
    ]
```

- - - 

## 更新
### 基于ID更新

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">方法：</td>
        <td width="500px" colspan="2">updateById(URI，object)</td>
    </tr>
    <tr align="center">
        <td>描述：</td>
        <td colspan="2">更新实体，需要包含主键ID。支持更新主实体和子实体。同时更新主实体和子实体时需要包含主实体主键ID，
        子实体根据_status状态进行插入、更新或删除。单独更新子实体时，需要包含子实体主键ID</td>
    </tr>
    <tr align="center">
        <td>入参：</td>
        <td colspan="2"></td>
    </tr>
    <tr align="center">
        <td>名称</td>
        <td>含义</td>
        <td>示例</td>
    </tr>
    <tr align="center">
        <td>URI</td>
        <td>实体统一资源标识符</td>
        <td>developplatform.AX000888.PX012991</td>
    </tr>
    <tr align="center">
        <td>object</td>
        <td>实体对象（更新字段内容），需要包含主键ID。 对子实体的操作通过_status属性标识：支持Insert(新增)、
        Update(更新)、Delete(删除)</td>
        <td>{id:3791337987775664129,firstName:"Bill", lastName:"Gates", age:62, eyeColor:"blue",
        tabpane0List:[{favor:"football",_status:"Insert"},{id:3791337987775664126,favor:"basketball",_status:"Update"}]}</td>
    </tr>
    <tr align="center">
        <td>返回值：</td>
        <td colspan="2">空</td>
    </tr>  
</table>

#### 示例

```
var object = {id:"0cddce5165194dddbb16bf75566e8667",name:"ppp",bustype:"1639837036187904",item41d:"45gty",
pX000008_tabpane0List:[{hasDefaultInit:true,item20l:"www",_status:"Insert"},{id:"8f900a6d08dc4d44b506f05dc74dc865",
_status:"Delete"}]};
var res = ObjectStore.updateById("developplatform.AX000003.PX000008",object);
```
```
//JavaScript对象的JSON串示例
{
        "id":"0cddce5165194dddbb16bf75566e8667",
        "name":"ppp",
        "bustype":"1639837036187904",
        "item41d":"45gty",
        "pX000008_tabpane0List":[
            {
                "hasDefaultInit":true,
                "item20l":"ppp",
                "id":"79072a33162b4f7ab177000977fcc8ac",
                "meta_fk":"0cddce5165194dddbb16bf75566e8667",
                "pubts":"Mar 14, 2020 3:46:49 PM"
            }
        ],
        "modifier":"xxx",
        "modifiedtime":"Mar 14, 2020 3:46:54 PM",
        "pubts":"Mar 14, 2020 3:46:49 PM"
 }
```
- - - 

### 批量更新

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">方法：</td>
        <td width="500px" colspan="2">updateBatch(URI，objectList)</td>
    </tr>
    <tr align="center">
        <td>描述：</td>
        <td colspan="2">批量更新实体，支持更新主实体和子实体。同时更新主实体和子实体时需要包
        含主实体主键ID，子实体根据_status状态进行插入、更新或删除。单独更新子实体时，需要包含子实体主键ID</td>
    </tr>
    <tr align="center">
        <td>入参：</td>
        <td colspan="2"></td>
    </tr>
    <tr align="center">
        <td>名称</td>
        <td>含义</td>
        <td>示例</td>
    </tr>
    <tr align="center">
        <td>URI</td>
        <td>实体统一资源标识符</td>
        <td>developplatform.AX000888.PX012991</td>
    </tr>
    <tr align="center">
        <td>object</td>
        <td>实体对象（更新字段内容），需要包含主键ID。对子实体的操作通过_status属性标识：支持Insert(新增)、
        Update(更新)、Delete(删除)</td>
        <td>[{id:3791337987775664129,firstName:"Bill", lastName:"Gates", age:62, eyeColor:"blue",
        tabpane0List:[{favor:"football",_status:"Insert"},{id:3791337987775664126,favor:"basketball",_status:"Update"}]},
            {id:3791337987775664123,firstName:"Andrew", lastName:"Jordon", age:32, eyeColor:"blue",
            tabpane0List:[{favor:"football",_status:"Insert"},{id:3791337987775664126,favor:"basketball",
            _status:"Delete"}]}]</td>
    </tr>
    <tr align="center">
        <td>返回值：</td>
        <td colspan="2">更新后的实体</td>
    </tr>  
</table>

#### 示例

```
  var object = [{id:"0cddce5165194dddbb16bf75566e8667",name:"ttt",bustype:"1639837036187904",item41d:"45gty",pX000008_tabpane0List:[{hasDefaultInit:true,item20l:"ttt",_status:"Insert"},{id:"79072a33162b4f7ab177000977fcc8ac",_status:"Delete"}]},{id:"1227ee93a5564f2e8c3b228e67b076c7",name:"yyy",bustype:"1639837036187904",item41d:"45gty",pX000008_tabpane0List:[{hasDefaultInit:true,item20l:"www",_status:"Insert"},{id:"cc784d51fcf042f0a26e02c8e3a4c2b4",_status:"Delete"},{id:"7eeaecc36344454395469157f0414654",item20l:"yyyy",_status:"Delete"}]}];
    var res = ObjectStore.updateBatch("developplatform.AX000003.PX000008",object); 
```

```
[
        {
            "id":"0cddce5165194dddbb16bf75566e8667",
            "name":"ttt",
            "bustype":"1639837036187904",
            "item41d":"45gty",
            "pX000008_tabpane0List":[
                {
                    "hasDefaultInit":true,
                    "item20l":"ttt",
                    "id":"830185ce91cc478087473de45f499b55",
                    "meta_fk":"0cddce5165194dddbb16bf75566e8667",
                    "pubts":"Mar 14, 2020 4:08:39 PM"
                }
            ],
            "modifier":"xxx",
            "modifiedtime":"Mar 14, 2020 4:08:39 PM",
            "pubts":"Mar 14, 2020 4:08:39 PM"
        },
        {
            "id":"1227ee93a5564f2e8c3b228e67b076c7",
            "name":"yyy",
            "bustype":"1639837036187904",
            "item41d":"45gty",
            "pX000008_tabpane0List":[
                {
                    "hasDefaultInit":true,
                    "item20l":"www",
                    "id":"290985a577154708a62dcea4621b03ca",
                    "meta_fk":"1227ee93a5564f2e8c3b228e67b076c7",
                    "pubts":"Mar 14, 2020 4:08:48 PM"
                }
            ],
            "modifier":"xxx",
            "modifiedtime":"Mar 14, 2020 4:08:48 PM",
            "pubts":"Mar 14, 2020 4:08:48 PM"
        }
    ]
```