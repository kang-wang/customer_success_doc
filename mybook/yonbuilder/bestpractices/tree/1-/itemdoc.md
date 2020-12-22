## 项目档案

### 功能目标

以【左树右卡】系统预制模板实现,
右侧卡片修改为主子页面

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/34.png"/>
</div>
<p align="center">效果图</p>

### 创建应用

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/1.png"/>
</div>
<p align="center">图 1</p>

### 元数据

#### 项目档案

操作 | 描述 | | | ||
---|---|---|---|---|---
名称 | 项目档案 |  |  |  |
编码 | itemdoc |  |  |  |
父实体 |  |  |  |  |
引用接口 | 树型结构、自动编码 |  |  |  |
|属性 | 编码 | 名称 | 类型 | 引用 
| |name | 名称 |  文本| 
| |Unit | 物料计量单位 |  单选引用| 物料计量单位
| |workload | 设计工程量 |  数值| 


#### 工程特征

操作 | 描述 | | | ||
---|---|---|---|---|---
名称 | 工程特征 |  |  |  |
编码 | project_trait |  |  |  |
父实体 | 项目档案 |  |  |  |
引用接口 |  |  |  |  |
|属性 | 编码 | 名称 | 类型 | 引用 
| |name | 特征值名称 |  文本| 
| |Unit | 物料计量单位 |  单选引用| 物料计量单位
| |	trait_value | 特征值 |  文本| 



### 功能实现

#### 新建页面
新建左树右卡页面,注意勾选生产参照

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/2.png"/>
</div>
<p align="center">图 2</p>

发布参照

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/3.png"/>
</div>
<p align="center">图 3</p>


#### 修改布局

进入页面设计器

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/4.png"/>
</div>
<p align="center">图 4</p>

根据图5位置新建多页签

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/5.png"/>
</div>
<p align="center">图 5</p>


根据图6位置新建表单

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/6.png"/>
</div>
<p align="center">图 6</p>


选中多页签，右键打开编辑器，Ctrl+C【复制内容】，

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/7.png"/>
</div>
<p align="center">图 7</p>


选中表单，右键打开编辑器，记录nid

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/8.png"/>
</div>
<p align="center">图 8</p>


多页签编辑器内容覆盖表单内容,记录的nid替换复制的内容


<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/9.png"/>
</div>
<p align="center">图 9</p>

删除原有多页签

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/10.png"/>
</div>
<p align="center">图 10</p>

选中多页签，新增表格

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/11.png"/>
</div>
<p align="center">图 11</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/12.png"/>
</div>
<p align="center">图 12</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/13.png"/>
</div>
<p align="center">图 13</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/14.png"/>
</div>
<p align="center">图 14</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/15.png"/>
</div>
<p align="center">图 15</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/16.png"/>
</div>
<p align="center">图 16</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/24.png"/>
</div>
<p align="center">图 17</p>

#### 调整布局

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/18.png"/>
</div>
<p align="center">图 18</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/19.png"/>
</div>
<p align="center">图 19</p>

配置工程特征物料参照

- 复制物料计量单位的cRefType

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/20.png"/>
</div>
<p align="center">图 20</p>

- 编辑工程特征的物料计量单位，粘贴复制的cRefType
增加   "cRefRetId": "{\"Unit\":\"id\"}",

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/21.png"/>
</div>
<p align="center">图 21</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/23.png"/>
</div>
<p align="center">图 22</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/33.png"/>
</div>
<p align="center">图 23</p>

- 增加增行按钮

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/25.png"/>
</div>
<p align="center">图 24</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/26.png"/>
</div>
<p align="center">图 25</p>

修改按钮编码为 btnAddRow+表格数据源编码
目的：利用系统预制，控制按钮显示

数据源编码：project_trait01

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/29.png"/>
</div>
<p align="center">图 26</p>

修改按钮cItemName和uikey 为btnAddRowproject_trait01

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/30.png"/>
</div>
<p align="center">图 27</p>


- 增加删行按钮

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/28.png"/>
</div>
<p align="center">图 28</p>

修改按钮编码为 btnDeleteRow+表格数据源编码
目的：利用系统预制，控制按钮显示

修改按钮cItemName和uikey 为btnDeleteRowproject_trait01

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/31.png"/>
</div>
<p align="center">图 29</p>

- 保存 

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/22.png"/>
</div>
<p align="center">图 30</p>


### 函数扩展

#### 表格增行/删行事件

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/32.png"/>
</div>
<p align="center">图 31</p>

```
function (event) {
  var viewModel = this;
  var gridModel = viewModel.getGridModel();
  
  //增行事件 btnAddRowproject_trait01为增行按钮编码
  viewModel.get('btnAddRowproject_trait01').on('click',function(){
    gridModel.appendRow({});
  });
  
  
  //删行事件  btnDeleteRowproject_trait01为删行按钮编码
  viewModel.get('btnDeleteRowproject_trait01').on('click',function(params){
    gridModel.deleteRows([params.index])
  });
} 

```


### 测试

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/17.png"/>
</div>
<p align="center">图 32</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/1-/images/34.png"/>
</div>
<p align="center">图 33</p>







