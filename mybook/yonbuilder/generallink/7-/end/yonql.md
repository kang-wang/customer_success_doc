# YonQL使用指南

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
        <td width="150px">含义</td>
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

## 删除

### 删除单个实体

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">方法：</td>
        <td width="500px" colspan="2">deleteById（URI，id）</td>
    </tr>
    <tr align="center">
        <td>描述：</td>
        <td colspan="2">逻辑删除实体，需要包含主键ID。支持删除主实体和子实体。如果删除的是主实体，则级联删除子实体</td>
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
        <td>主实体需要主键ID、pubts。子实体不校验时间戳，仅需要ID</td>
        <td>{id:"0cddce5165194dddbb16bf75566e8667",pubts:"2020-03-14 16:08:39",pX000008_tabpane0List:[{id:"830185ce91cc478087473de45f499b55"},{id:"f4857dc2f70c4ab285119a88fce3ac4b"}]}</td>
    </tr>
    <tr align="center">
        <td>返回值：</td>
        <td colspan="2">空</td>
    </tr>  
</table>

#### 示例

```
var object = {id:"0cddce5165194dddbb16bf75566e8667",pubts:"2020-03-14 16:08:39",pX000008_tabpane0List:[{id:"830185ce91cc478087473de45f499b55"},{id:"f4857dc2f70c4ab285119a88fce3ac4b"}]};
var res = ObjectStore.deleteById("developplatform.AX000003.PX000008",object); 
```

### 条件删除实体

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">方法：</td>
        <td width="500px" colspan="2">deleteByMap（URI，columnMap）</td>
    </tr>
    <tr align="center">
        <td>描述：</td>
        <td colspan="2">基于Map条件逻辑删除实体。支持删除主实体和子实体。如果删除的是主实体，则级联删除子实体</td>
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
        <td>条件值，及关联的子实体。association字段及association关联的子实体可选，如果不填则只删除主实体。否则查询主实体及相关的子实体</td>
        <td>{name:"qqq",creator:"xxx",association:["pX000008_tabpane0List"]}</td>
    </tr>
    <tr align="center">
        <td>返回值：</td>
        <td colspan="2">空</td>
    </tr>  
</table>

#### 示例

```
   var object = {name:"qqq",creator:"xxx",association:["pX000008_tabpane0List"]};
    var res = ObjectStore.deleteByMap("developplatform.AX000003.PX000008",object); 
```

### 基于ID批量删除实体

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">方法：</td>
        <td width="500px" colspan="2">deleteBatch（URI，objectList）</td>
    </tr>
    <tr align="center">
        <td>描述：</td>
        <td colspan="2">基于多个ID逻辑删除实体。如果删除的是主实体，则级联删除子实体</td>
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
        <td>id列表</td>
        <td>[{id:"1227ee93a5564f2e8c3b228e67b076c7",pubts:"2020-03-14 16:08:48",pX000008_tabpane0List:[{id:"290985a577154708a62dcea4621b03ca",_status:"Delete"}]},{id:"39dccc83fca0468d98ffc485d8d09d11",pubts:"2020-03-14 16:43:16",pX000008_tabpane0List:[{id:"99143865e4b24689bee0d6adf77f0426",_status:"Delete"},{id:"9924fa3fa63c47c1b56d69edb983a90f",_status:"Delete"}]}]</td>
    </tr>
    <tr align="center">
        <td>返回值：</td>
        <td colspan="2">空</td>
    </tr>  
</table>

#### 示例

```
    var object = [{id:"1227ee93a5564f2e8c3b228e67b076c7",pubts:"2020-03-14 16:08:48",pX000008_tabpane0List:[{id:"290985a577154708a62dcea4621b03ca",_status:"Delete"}]},{id:"39dccc83fca0468d98ffc485d8d09d11",pubts:"2020-03-14 16:43:16",pX000008_tabpane0List:[{id:"99143865e4b24689bee0d6adf77f0426",_status:"Delete"},{id:"9924fa3fa63c47c1b56d69edb983a90f",_status:"Delete"}]}];
    var res = ObjectStore.deleteBatch("developplatform.AX000003.PX000008",object);  
```

## 查询

### 基于ID查询

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">方法：</td>
        <td width="500px" colspan="2">deleteBatch（URI，objectList）</td>
    </tr>
    <tr align="center">
        <td>描述：</td>
        <td colspan="2">基于多个ID逻辑删除实体。如果删除的是主实体，则级联删除子实体</td>
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
        <td>id</td>
        <td>实体对象主键ID，及关联的子实体。compositions字段可选，如果不填则只查询主实体。否则查询主实体及相关的子实体。compostions中的name字段是关联的子实体。支持多级查询</td>
        <td>{"id":"0cddce5165194dddbb16bf75566e8667","compositions":[{"name":"pX000008_tabpane0List","compositions":[
            {"name":"","compositions":[]}]},{"name":"pX000008_tabpane0List","compositions":[ {
    </tr>
    <tr align="center">
        <td>返回值：</td>
        <td colspan="2">JSON</td>
    </tr>  
</table>

#### 示例

#### 只查询主实体示例
```
    var object = {id:"0cddce5165194dddbb16bf75566e8667"};
    var res = ObjectStore.selectById("developplatform.AX000003.PX000008",object); 
```
##### 返回值
```
{
    "returncount": 0,
    "verifystate": 0,
    "creator": "xxx",
    "isWfControlled": true,
    "modifier": "xxx",
    "bustype": "1639837036187904",
    "item185h": false,
    "modifiedtime": "Mar 14, 2020 4:43:15 PM",
    "item41d": "45gty",
    "name": "qqq",
    "id": "c57c7745c67941ad8f39ab429b6baca4",
    "creationtime": "Mar 14, 2020 4:43:15 PM",
    "pubts": "Mar 14, 2020 4:43:15 PM"
  }
```

#### 查询主子实体示例

```
    var object = {
    id:"5830f15a5fb04317b854d4c7e895d4a8",
    compositions:[
        {
            name:"pX000008_tabpane0List",
            compositions:[
              
            ]
        }
    ]
    };
    var res = ObjectStore.selectById("developplatform.AX000003.PX000008",object); 
```
##### 返回值

```
{
    "returncount":0,
    "verifystate":0,
    "creator":"07f90f73-24b0-41fa-83b2-8108d99cb98e",
    "isWfControlled":true,
    "modifier":"07f90f73-24b0-41fa-83b2-8108d99cb98e",
    "pX000008_tabpane0List":[
        {
            "item20l":"mmm",
            "id":"1e9286ec6bb84d3db29b5721beb26f0b",
            "pubts":"Mar 25, 2020 2:08:46 PM",
            "meta_fk":"5830f15a5fb04317b854d4c7e895d4a8"
        }
    ],
    "bustype":"1639837036187904",
    "item185h":false,
    "modifiedtime":"Mar 25, 2020 2:06:02 PM",
    "item41d":"45gty",
    "name":"qqq",
    "id":"5830f15a5fb04317b854d4c7e895d4a8",
    "creationtime":"Mar 25, 2020 2:06:02 PM",
    "pubts":"Mar 25, 2020 2:06:02 PM"
}
```

### YonQL实体查询

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">方法：</td>
        <td width="500px" colspan="2">queryByYonQL（sql)</td>
    </tr>
    <tr align="center">
        <td>描述：</td>
        <td colspan="2"></td>
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
        <td>sql</td>
        <td>YonQL</td>
        <td>select * from online0205.treeucfbase.treeucfbase_Treetable where parent like 'root'</td>
    </tr>
    <tr align="center">
        <td>返回值：</td>
        <td colspan="2">JSON</td>
    </tr>  
</table>

#### 示例

```
ObjectStore.queryByYonQL('select * from online0205.treeucfbase.treeucfbase_Treetable')
```

### 批量ID实体查询

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">方法：</td>
        <td width="500px" colspan="2">queryByYonQL（sql)</td>
    </tr>
    <tr align="center">
        <td>描述：</td>
        <td colspan="2"></td>
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
        <td>idList</td>
        <td>实体对象主键ID，及关联的子实体。association字段可选，如果不填则只查询主实体。否则查询主实体及相关的子实体</td>
        <td>{ids:["5830f15a5fb04317b854d4c7e895d4a8","2b4bd236460b4a98bd2881ee60549c40","2b84ee085d2949d5a88c8499c6d74a6e"],
            compositions:[{name:"pX000008_tabpane0List1",compositions:[{name:"pX000008_tabpane0List3",
            compositions:[{name:"pX000008_tabpane0List6"}]},{name:"pX000008_tabpane0List4",
            compositions:[]}]},{name:"pX000008_tabpane0List2",compositions:[{name:"pX000008_tabpane0List5",
            compositions:[]}]}]}</td>
    </tr>
    <tr align="center">
        <td>返回值：</td>
        <td colspan="2">JSON</td>
    </tr>  
</table>

#### 只查询主实体示例

```
    var object = {ids:["c57c7745c67941ad8f39ab429b6baca4","152bd644cc0741088cb43449faf31637"]};
    var res = ObjectStore.selectBatchIds("developplatform.AX000003.PX000008",object); 
```

##### 返回值

```
[{
    "returncount": 0,
    "verifystate": 0,
    "creator": "xxx",
    "isWfControlled": true,
    "modifier": "xxx",
    "bustype": "1639837036187904",
    "item185h": false,
    "modifiedtime": "Mar 12, 2020 2:00:44 PM",
    "item41d": "45gty",
    "name": "qqq",
    "id": "152bd644cc0741088cb43449faf31637",
    "creationtime": "Mar 12, 2020 2:00:44 PM",
    "pubts": "Mar 12, 2020 2:00:44 PM"
  }, {
    "returncount": 0,
    "verifystate": 0,
    "creator": "xxx",
    "isWfControlled": true,
    "modifier": "xxx",
    "bustype": "1639837036187904",
    "item185h": false,
    "modifiedtime": "Mar 14, 2020 4:43:15 PM",
    "item41d": "45gty",
    "name": "qqq",
    "id": "c57c7745c67941ad8f39ab429b6baca4",
    "creationtime": "Mar 14, 2020 4:43:15 PM",
    "pubts": "Mar 14, 2020 4:43:15 PM"
  }]
```

#### 主子实体查询

```
    var object = {
    ids:["5830f15a5fb04317b854d4c7e895d4a8","2b4bd236460b4a98bd2881ee60549c40","2b84ee085d2949d5a88c8499c6d74a6e"],
    compositions:[
        {
            name:"pX000008_tabpane0List",
            compositions:[
              
            ]
        }
    ]
    };
    var res = ObjectStore.selectBatchIds("developplatform.AX000003.PX000008",object); 
```

### 条件查询

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">方法：</td>
        <td width="500px" colspan="2">selectByMap（URI，columnMap）</td>
    </tr>
    <tr align="center">
        <td>描述：</td>
        <td colspan="2"></td>
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
        <td>columnMap</td>
        <td>条件值，compositions可选，如果不填，只查询主实体。如果关联，查询指定关联的子实体</td>
        <td>{name:"qqq",creator:"xxx",compositions:[ {name:"pX000008_tabpane0List",compositions:[
            ]}]}</td>
    </tr>
    <tr align="center">
        <td>返回值：</td>
        <td colspan="2">JSON</td>
    </tr>  
</table>

#### 只查询主实体示例

```
var object = {name:"qqq",creator:"xxx"};
    var res = ObjectStore.selectByMap("developplatform.AX000003.PX000008",object);
```

#### 查询主子实体示例

```
var object ={
   name:"qqq",
   creator:"xxx",
   compositions:[
     {
            name:"pX000008_tabpane0List",
            compositions:[
              
            ]
       }
   ]
  };
var res = ObjectStore.selectByMap("developplatform.AX000003.PX000008",object);
```

### 其他常用查询

|  | 单表查询 | select * from   online0205.treeucfbase.treeucfbase_Treetable |  |
| --- | --- | --- | --- |
| 支持的比较符 | like | select * from   online0205.treeucfbase.treeucfbase_Treetable where parent like 'root' | like 不需要加%,会自动转换成 like %root%,如果加上%，会被转义成 %\\%root\\%% |
|  | leftlike | select *  from   online0205.treeucfbase.treeucfbase_Treetable where parent leftlike 'root' |  like 'root%',不需要加% |
|  | rightlike | select *  from   online0205.treeucfbase.treeucfbase_Treetable where parent rightlike 'root' |  like '%root',不需要加% |
|  | not like | 不支持 |  |
|  | 等于 | select * from   online0205.treeucfbase.treeucfbase_Treetable where parent= 'root' |  |
|  | 不等于 | select * from   online0205.treeucfbase.treeucfbase_Treetable where parent != 'root' |  |
|  | 不等于 | select * from   online0205.treeucfbase.treeucfbase_Treetable where parent <> 'root' |  |
|  | 大于 | select * from   online0205.treeucfbase.treeucfbase_Treetable where level>1 |  |
|  | 大于等于 | select * from   online0205.treeucfbase.treeucfbase_Treetable where level>=2 |  |
|  | 小于 | select * from   online0205.treeucfbase.treeucfbase_Treetable where level<3 |  |
|  | 小于等于 | select * from   online0205.treeucfbase.treeucfbase_Treetable where level<=2 |  |
|  | between and  | select * from   online0205.treeucfbase.treeucfbase_Treetable where level between 1 and 3 |  |
|  | not between and  | 不支持，改写为 field>value2 and   field<value1 |  |
|  | in | select * from   online0205.treeucfbase.treeucfbase_Treetable where level in(1,2,3) |  |
|  | not in | select * from   online0205.treeucfbase.treeucfbase_Treetable where level not in(1,2,3) |  |
|  | is null | select * from   online0205.treeucfbase.treeucfbase_Treetable where parent is null | parent is null or parent='' |
|  | is not null | select * from   online0205.treeucfbase.treeucfbase_Treetable where parent is not null | parent is not null and parent !='' |
|  | 分页 | select * from   online0205.treeucfbase.treeucfbase_Treetable limit 0,2 |  |
|  | 总条数 | select count(id) cnt from   online0205.treeucfbase.treeucfbase_Treetable  | 不能使用count(*),使用count(主键)，运行时会报错！ |
|  | 多条件查询 | select * from   online0205.treeucfbase.treeucfbase_Treetable where parent like 'root' and   (level=2 or treename=1) |  |
|  | in子查询 | select * from   online0205.treeucfbase.treeucfbase_Treeson1 where mainid in (select id from   online0205.treeucfbase.treeucfbase_Treetable where parent='root') |  |
|  | 动态类型 | select   dynatype(mainid,'online0205.treeucfbase.treeucfbase_Treetable',alias1),name,code,mainid.name   from online0205.treeucfbase.treeucfbase_Treeson1  | 自定义类型 |
| 关联查询 | left join | select mainid.parent,name,code   from online0205.treeucfbase.treeucfbase_Treeson1 t left join mainid t1 | 1）结果集不能使用t.*,必须写清楚属性名。运行时会报错<br />2）如果关联关系在元数据中存在，不需要写关联条件<br />3）select 的结果集里面，不能使用别名，如果是当前元数据，直接写属性名称，如果是关联属性的属性，写关联属性.属性名称。<br />最终执行的sql如下<br />select T0.name as `name`,T0.code as `code`,T1.parent_id   as `mainid_parent`<br />    from cf_Treeson10211c T0<br />    left join cf_Treetable0211c as T1 on (T0.mainid=T1.id); |
|  | left alone join | select mainid.parent,name,code   from online0205.treeucfbase.treeucfbase_Treeson1 t left alone join mainid t1   on t.mainid=t1.id  | select T0.name as `name`,T0.code   as `code`,T1.parent_id as `mainid_parent`<br />    from cf_Treeson10211c T0<br />    left join cf_Treetable0211c as T1 on (T0.mainid=T1.id); |
|  | inner join  | select mainid.parent,name,code   from online0205.treeucfbase.treeucfbase_Treeson1 t inner join mainid t1 |  |
|  | inner alone join | select mainid.parent,name,code   from online0205.treeucfbase.treeucfbase_Treeson1 t inner alone join mainid t1   on t.mainid=t1.id  |  |
|  | alone join | select mainid.parent,name,code   from online0205.treeucfbase.treeucfbase_Treeson1 t alone join mainid t1 on   t.mainid=t1.id  |  |
|  | 组合查询 | select   id,code,name,parent,(select name,code from Treeson1List) sonlist from   online0205.treeucfbase.treeucfbase_Treetable | 关联属性必须作为查询结果。比如默认父实体的id必须在结果集中存在。否则子实体查询不出来。 |
|  | 组合查询rel关联 | select   id,code,name,parent,(select name,code from Treeson1List   where id=parent) sonlist from   online0205.treeucfbase.treeucfbase_Treetable |  |

##### 注意事项

1. 子查询不推荐使用，性能差
1. 如果使用了函数，尽量给结果起别名，防止同名函数别名覆盖。
1. 公式导致性能变差
1. 函数转换后的语法为函数名(参数1,参数2...)，参数为 函数 或 元数据字段 或 常量。否则queryschema解析不了。
1. 对于常量运算，负数需要加上单引号，例如 mod(-5,2),应该写成mod('-5',2)
1. "distinct 去重
- 需要一个包含 distinct 聚合函数的查询字段。
- 该查询字段必须位于第一个位置。
7. 其他限制参考营销云开发手册










