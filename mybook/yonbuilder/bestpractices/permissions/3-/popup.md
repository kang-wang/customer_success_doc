## 功能点：阅读记录列表弹框

### 功能目标

- 列表页面通过弹框的方式，查看阅读记录

### 弹框知识点

#### 通过表格按钮打开一个页面
【异常记录列表】打开【阅读记录】页面

```
function (event) {
  var viewModel = this;
  //获取选中行的行号
  var line  = event.params.index;
  //获取选中行数据信息
  var abnormalevent = viewModel.getGridModel().getRow(line).id;
  //传递给被打开页面的数据信息
  let data = {
    billtype: 'VoucherList',// 单据类型
    billno: '43472ef5List',// 单据号
    params: {
      mode: 'browse', // (编辑态edit、新增态add、浏览态browse)
      //传参
      abnormalevent:abnormalevent
    },
  };
  //打开一个单据，并在当前页面显示
  cb.loader.runCommandLine('bill', data, viewModel);
}
```

#### 获取父页面传递参数并实现过滤
【阅读记录】页面获取【异常记录列表】传递的参数，并过滤数据

```
function (event) {
  var viewModel = this;
  var bh = viewModel.getParams().abnormalevent;
  viewModel.on('afterMount', function(){
    // 获取查询区模型
    const filtervm = viewModel.getCache('FilterViewModel'); 
    filtervm.on('afterInit', function () {
      // 进行查询区相关扩展
      filtervm.get('abnormalevent').getFromModel().setValue(bh);
      });
  });
} 
```

#### 关闭模态框
绑定【阅读记录】取消确定按钮点击可以关闭模态框

```
function(event){
    var viewModel = this;
    viewModel.communication({type:'modal',payload:{data:false}});
}
```

#### 弹出框获取父页面ViewModel

```
function(event){
    var viewModel = this;
    var parentViewModel = viewModel.getCache('parentViewModel');
}
```

### 阅读记录弹框功能实现

#### 【阅读记录列表】增加弹框按钮及动作

新增【异常记录列表】表格行按钮【阅读记录】

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/20.png"/>
</div>
<p align="center">图 1</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/21.png"/>
</div>
<p align="center">图 2</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/22.png"/>
</div>
<p align="center">图 3</p>


【阅读记录】按钮绑定点击事件

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/23.png"/>
</div>
<p align="center">图 4</p>

函数设计器中添加以下函数

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/24.png"/>
</div>
<p align="center">图 5</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/25.png"/>
</div>
<p align="center">图 6</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/26.png"/>
</div>
<p align="center">图 7</p>

```
function (event) {
  var viewModel = this;
  //获取选中行的行号
  var line  = event.params.index;
  //获取选中行数据信息
  var abnormalevent = viewModel.getGridModel().getRow(line).id;
  //传递给被打开页面的数据信息
  let data = {
    //TODO：填写单据类型及单据号
    billtype: 'VoucherList',// 单据类型
    billno: 'e3e52ae2',// 单据号
    params: {
      mode: 'browse', // (编辑态edit、新增态add、浏览态browse)
      //传参
      abnormalevent:abnormalevent
    },
  };
  //打开一个单据，并在当前页面显示
  cb.loader.runCommandLine('bill', data, viewModel);
}
```

### 【阅读记录】设置弹框及进行条件过滤

#### 设置模态框
将页面设置为模态框

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/27.png"/>
</div>
<p align="center">图 8</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/28.png"/>
</div>
<p align="center">图 9</p>

选中页面模板，点击右键，打开编辑，增加下列属性
```
  "templateType": "modal",
```
<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/29.png"/>
</div>
<p align="center">图 10</p>

改变模态框宽度并保存

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/30.png"/>
</div>
<p align="center">图 11</p>

#### 数据过滤

点击层级-》阅读记录-》新增前端函数

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/31.png"/>
</div>
<p align="center">图 12</p>

函数内容

```
function (event) {
  var viewModel = this;
  var bh = viewModel.getParams().abnormalevent;
  viewModel.on('afterMount', function(){
    // 获取查询区模型
    const filtervm = viewModel.getCache('FilterViewModel'); 
    filtervm.on('afterInit', function () {
      // 进行查询区相关扩展
      filtervm.get('abnormalevent').getFromModel().setValue(bh);
      });
  });
}

```


#### 关闭模态框
绑定【阅读记录】【取消】【确定】按钮点击可以关闭模态框

```
function(event){
    var viewModel = this;
    viewModel.communication({type:'modal',payload:{data:false}});
}
```

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/36.png"/>
</div>
<p align="center">图 13</p>

### 调整页面

新建调整参照

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/48.png"/>
</div>
<p align="center">图 14</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/47.png"/>
</div>
<p align="center">图 15</p>

阅读记录页面调整

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/44.png"/>
</div>
<p align="center">图 16</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/45.png"/>
</div>
<p align="center">图 17</p>

### 测试


<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/33.png"/>
</div>
<p align="center">图 18</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/34.png"/>
</div>
<p align="center">图 19</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/35.png"/>
</div>
<p align="center">图 20</p>












