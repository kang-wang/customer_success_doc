## 材料梳理

### 功能目标

左树右表，单页面操作

### 元数据

#### 材料梳理

操作 | 描述 | | | ||
---|---|---|---|---|---
名称 | 材料梳理 |  |  |  |
编码 | material_clearup |  |  |  |
父实体 |  |  |  |  |
引用接口 | 自动编码 |  |  |  |
|属性 | 编码 | 名称 | 类型 | 引用 
| |item_wbs | 项目档案 |  单选引用| 项目档案
| |name | 材料名称 |  文本| 
| |Product | 物料 |  单选引用| 物料
| |design_num | 设计数量 |  数值| 

### 功能实现

#### 新建页面

新建【左树右表】页面

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/1.png"/>
</div>
<p align="center">图 1</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/2.png"/>
</div>
<p align="center">图 2</p>

效果显示

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/3.png"/>
</div>
<p align="center">图 3</p>


#### 调整布局

进入【材料梳理】页面设计器

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/4.png"/>
</div>
<p align="center">图 4</p>

新增编辑按钮

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/5.png"/>
</div>
<p align="center">图 5</p>

增加底部栏及按钮

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/6.png"/>
</div>
<p align="center">图 6</p>

右键【DIV块】点击【打开编辑器】，修改uitype、cControlType属性值为：groupcontainer

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/7.png"/>
</div>
<p align="center">图 7</p>

右键【DIV块】新增【表单】控件

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/8.png"/>
</div>
<p align="center">图 8</p>

右键【表单】点击【打开编辑器】 复制nid属性的值。记录至文本文件中备用

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/9.png"/>
</div>
<p align="center">图 9</p>

1. 右键【底部栏】点击【打开编辑器】赋值(Ctrl+A   Ctrl+C)所有的属性，关闭弹框;
2. 右键【表单】点击【打开编辑器】Ctrl+A 全部选中然后 Delete 删除所有属性。 Ctrl+V 复制【底部栏】
的属性至【表单】;
3. 将记录的nid属性值，覆盖【底部栏】里面的nid 。然后选中整个【底部栏】删除

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/10.png"/>
</div>
<p align="center">图 10</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/11.png"/>
</div>
<p align="center">图 11</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/12.png"/>
</div>
<p align="center">图 12</p>

还原【DIV块】uitype、cControlType属性值为：div

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/13.png"/>
</div>
<p align="center">图 13</p>

设置保存按钮规格类型为【主按钮】

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/14.png"/>
</div>
<p align="center">图 14</p>

### 函数扩展

#### 【材料梳理单卡】做成弹框

设置【材料梳理单卡】为模态框
<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/15.png"/>
</div>
<p align="center">图 15</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/16.png"/>
</div>
<p align="center">图 16</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/17.png"/>
</div>
<p align="center">图 17</p>

1. 删除底部栏内的字段控件，下图为删除后效果
2. 删除整个表单头部栏

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/18.png"/>
</div>
<p align="center">图 18</p>

3. 删除标题,修改标题(按下图操作)

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/30.png"/>
</div>
<p align="center">图 19</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/31.png"/>
</div>
<p align="center">图 20</p>

【材料梳理单卡】初始化函数增加样式，调整按钮显示位置

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/22.png"/>
</div>
<p align="center">图 21</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/20.png"/>
</div>
<p align="center">图 22</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/21.png"/>
</div>
<p align="center">图 23</p>

```
function (event) {
  var viewModel = this;
  loadStyle('.tab-bottom-txt{position: relative;height:30px;}')
  loadStyle('.alignRight{position:absolute;right:30px;}')
  
  function loadStyle(params){
    var headobj=document.getElementsByTagName('head')[0];
    var style = document.createElement('style');
    style.type = 'text/css';
    headobj.appendChild(style);
    style.sheet.insertRule(params, 0);
  }
} 

```

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/19.png"/>
</div>
<p align="center">图 24</p>

#### 编辑/取消按钮扩展

1. 点击编辑按钮,设置表格可编辑。底部按钮栏显示,表头工具栏隐藏
2. 点击取消按钮,刷新页面，设置表格不可编辑，设置底部栏隐藏，表头工具栏显示

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/23.png"/>
</div>
<p align="center">图 25</p>

```
function (event) {
  var viewModel = this;
  var gridModel = viewModel.getGridModel();
  //初始化设置底部栏隐藏
  viewModel.on('afterMount',function(){
    setlayoutDisplay('footer8bd',false);
  })
  //点击编辑按钮，工具栏隐藏，底部栏显示
  viewModel.get('button8kj').on('click',function(){
    setlayoutDisplay('TreeTableHeader',false);  //表头工具栏隐藏
    setlayoutDisplay('footer8bd',true);  //底部栏显示
    gridModel.setState('actionStatesVisible',false);  //表格按钮栏隐藏
    gridModel.setReadOnly(false);     //设置表格允许编辑
  })
  
  //点击取消刷新页面
  viewModel.get('button10ki').on('click',function(){
    viewModel.execute('refresh');    //刷新页面
    setlayoutDisplay('TreeTableHeader',true);  //表头工具栏显示
    setlayoutDisplay('footer8bd',false);  //底部栏隐藏
    gridModel.setState('actionStatesVisible',true);  //表格按钮栏显示
    gridModel.setReadOnly(true);  //设置表格不允许编辑
  })
  
  
  //设置布局的隐藏显示
  function setlayoutDisplay(cGroupCode,boolean){
    viewModel.execute('updateViewMeta',{code:cGroupCode,visible:boolean}); 
  }
}

```

- 上述函数功能解析

设置布局隐藏显示,
cGroupCode为容器编码

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/24.png"/>
</div>
<p align="center">图 26</p>

```
viewModel.execute('updateViewMeta',{code:cGroupCode,visible:boolean}); 
```

设置表格是否可编辑

```
viewModel.getGridModel().gridModel.setReadOnly(boolean);
```

刷新页面

```
viewModel.execute('refresh');
```

- 实现的效果

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/25.png"/>
</div>
<p align="center">图 27</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/26.png"/>
</div>
<p align="center">图 28</p>

#### 保存按钮扩展
点击保存按钮，更新保存的数据

新增前端函数

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/27.png"/>
</div>
<p align="center">图 29</p>

```
function (event) {
  var viewModel = this;
  var gridModel = viewModel.getGridModel();
  var proxy = cb.rest.DynamicProxy.create({
		settle: {
			url: 'bill/save',
			method: 'POST'
		}
    });
    //传参
    var param = gridModel.getDirtyData();
    var reqParams = {
      'billnum':'2d798483SingleCard',   //TODO：需要更改
      'data':param
    }
    proxy.settle(reqParams, function(err, result) {
        if (err) {
          cb.utils.alert(err.message, 'error');
          return;
        }else{
          cb.utils.alert('保存成功');
          viewModel.execute('refresh');
          setlayoutDisplay('TreeTableHeader',true);
          setlayoutDisplay('footer8bd',false);
          //设置表格不允许编辑
          gridModel.setReadOnly(true);
        }
    });
    
    
  //设置布局的隐藏显示
  function setlayoutDisplay(cGroupCode,boolean){
    viewModel.execute('updateViewMeta',{code:cGroupCode,visible:boolean}); 
  }
}
```

如何查看billnum?

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/28.png"/>
</div>
<p align="center">图 30</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/29.png"/>
</div>
<p align="center">图 31</p>


### 测试
选择左侧分类，点击新增

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/32.png"/>
</div>
<p align="center">图 32</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/33.png"/>
</div>
<p align="center">图 33</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/34.png"/>
</div>
<p align="center">图 34</p>

点击编辑

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/35.png"/>
</div>
<p align="center">图 35</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/36.png"/>
</div>
<p align="center">图 36</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/tree/2-/images/37.png"/>
</div>
<p align="center">图 37</p>



















 





















