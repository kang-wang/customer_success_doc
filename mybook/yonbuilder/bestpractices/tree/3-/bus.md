## 业主清单

### 功能目标

树型表+主子孙

### 元数据

#### 材料梳理

操作 | 描述 | | | ||
---|---|---|---|---|---
名称 | 材料梳理 |  |  |  |
编码 | material_clearup |  |  |  |
父实体 |  |  |  |  |
引用接口 | 自动编码 / 树型结构 |  |  |  |
|属性 | 编码 | 名称 | 类型 | 引用 
| |Unit | 物料计量单位 |  单选引用| 物料计量单位
| |num | 数量 |  数值| 
| |singleprice | 单价 |  数值| 
| |name | 清单名称 |  数值| 
| |sumprice | 金额 |  数值| 


#### 挂接WBS

操作 | 描述 | | | ||
---|---|---|---|---|---
名称 | 挂接WBS |  |  |  |
编码 | wbs_gj |  |  |  |
父实体 | 业主清单 |  |  |  |
引用接口 | |  |  |  |
|属性 | 编码 | 名称 | 类型 | 引用 
| |item_wbs | 项目WBS |  单选引用| 项目档案
| |qingdandanwei | 清单单位 |  文本| 
| |qingdanguajieshuliang | 清单挂接数量 |  数值| 


#### 材料挂接

操作 | 描述 | | | ||
---|---|---|---|---|---
名称 | 材料挂接 |  |  |  |
编码 | product_gj |  |  |  |
父实体 | 挂接WBS |  |  |  |
引用接口 | |  |  |  |
|属性 | 编码 | 名称 | 类型 | 引用 
| |Product | 物料 |  单选引用| 物料
| |Unit | 计量单位 |  单选引用| 物料计量单位
| |num | 设计量 |  数值| 



### 功能实现

#### 新建树型表【业主清单】

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/1.png"/>
</div>
<p align="center">图 1</p>

勾选生产参照

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/2.png"/>
</div>
<p align="center">图 2</p>

发布参照

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/22.png"/>
</div>
<p align="center">图 3</p>

删除【业主清单单卡】

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/3.png"/>
</div>
<p align="center">图 4</p>

进入【业主清单】页面设计器，调整布局


<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/27.png"/>
</div>
<p align="center">图 5</p>



#### 新建主子孙【业主清单主子孙】

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/4.png"/>
</div>
<p align="center">图 6</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/5.png"/>
</div>
<p align="center">图 7</p>

删除上级分类

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/23.png"/>
</div>
<p align="center">图 8</p>

设置参照

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/24.png"/>
</div>
<p align="center">图 9</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/25.png"/>
</div>
<p align="center">图 10</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/26.png"/>
</div>
<p align="center">图 11</p>


删除【业主清单主子孙列表】

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/6.png"/>
</div>
<p align="center">图 12</p>


#### 【业主清单】关联【业主清单主子】

进入设计器

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/7.png"/>
</div>
<p align="center">图 13</p>

设置关联页面

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/8.png"/>
</div>
<p align="center">图 14</p>

效果演示

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/9.png"/>
</div>
<p align="center">图 15</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/10.png"/>
</div>
<p align="center">图 16</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/11.png"/>
</div>
<p align="center">图 17</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/12.png"/>
</div>
<p align="center">图 18</p>


### 函数扩展

功能目标：选中子表后，带出孙表数据。

新建前端函数

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/13.png"/>
</div>
<p align="center">图 19</p>

#### 前端函数扩展

```
function (event) {
  var viewModel = this;
  var gridModelCh = viewModel.get('wbs_gj01List'); //子表数据
  var gridModelChCh = viewModel.get('product_gj01List'); //孙表数据
  //挂接WBS
  gridModelCh.on("afterCellValueChange",function(params){
    if(params.cellName=='item_wbs_name'&&params.value!=""){
      //要请求后台拉取孙表数据
      var promise = new cb.promise();
      //请查看下一步后端函数的id
      cb.rest.invokeFunction("14bf120c800f4b918df5f12af5346d31", {id:params.value.id},
      function(err, res) {
        if(err!=null){
          cb.utils.alert('拉取孙表数据错误');
        }else{
          if(res.res!=null&&res.res.length>0){
            var totals = 0;
            res.res.forEach((data)=>{
              //为了避免重复插入行，根据子表id判断是否为要插入的子表
              if(data.product_gj01Fk==params.value.id){
                  gridModelChCh.appendRow(data);
                  totals+=data.num;
              }
            });
            if(totals>0&&res.res[0].product_gj01Fk==params.value.id){
                gridModelCh.setCellValue(params.rowIndex,"qingdanguajieshuliang",totals);
            }
          }
        }
        promise.resolve();
      })
    }
  });
}
```

#### 前端功能拆分--知识点

多个表格的情况下获取指定表格

```
function (event) {
  var viewModel = this;
  var gridModel = viewModel.get('wbs_gj01List');
}

```
<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/14.png"/>
</div>
<p align="center">图 20</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/15.png"/>
</div>
<p align="center">图 21</p>


#### 后端函数

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/16.png"/>
</div>
<p align="center">图 22</p>

如何获取后端函数id ?
<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/17.png"/>
</div>
<p align="center">图 23</p>

```
let AbstractAPIHandler = require('AbstractAPIHandler');
  class MyAPIHandler extends AbstractAPIHandler {
   execute(request){
    var item_wbs = request.id;
    var sql = "select item_wbs as product_gj01Fk,Product,Product.name as Product_name ,"+
    "design_num as num from GT11068AT183.GT11068AT183.material_clearup01 where item_wbs='"+item_wbs+"'";
    var res = ObjectStore.queryByYonQL(sql);
   return {res:res};
 }
}
exports({"entryPoint":MyAPIHandler});
```

### 测试

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/18.png"/>
</div>
<p align="center">图 24</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/19.png"/>
</div>
<p align="center">图 25</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/20.png"/>
</div>
<p align="center">图 26</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/21.png"/>
</div>
<p align="center">图 27</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/3-/images/28.png"/>
</div>
<p align="center">图 28</p>






