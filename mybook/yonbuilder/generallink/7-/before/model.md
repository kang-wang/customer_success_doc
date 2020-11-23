## 弹出卡片模态框

### 第一步： 进去卡片设计器,在层级页签点击右键【页面模型】，插入【表单】

<div align=center>
<img src="/mybook/yonbuilder/generallink/7-/before/images/1.png"/>
</div>
<p align="center">图 1</p>

### 第二步：选中新建的表单，向表单中插入内容

<div align=center>
<img src="/mybook/yonbuilder/generallink/7-/before/images/2.png"/>
</div>
<p align="center">图 2</p>

### 第三步：设置好后右键点击表单-打开编辑器

<div align=center>
<img src="/mybook/yonbuilder/generallink/7-/before/images/3.png"/>
</div>
<p align="center">图 3</p>

<div align=center>
<img src="/mybook/yonbuilder/generallink/7-/before/images/4.png"/>
</div>
<p align="center">图 4</p>

### 第四步：拖拽过来一个按钮,按钮绑定打开模态框事件

<div align=center>
<img src="/mybook/yonbuilder/generallink/7-/before/images/5.png"/>
</div>
<p align="center">图 5</p>

<div align=center>
<img src="/mybook/yonbuilder/generallink/7-/before/images/6.png"/>
</div>
<p align="center">图 6</p>

<div align=center>
<img src="/mybook/yonbuilder/generallink/7-/before/images/7.png"/>
</div>
<p align="center">图 7</p>

```

viewModel.communication({
    type: 'modal',
    payload: {
      mode: 'inner',
      groupCode: 'form24yd',  //表单的容器编码
      viewModel: viewModel
    }
  });

viewModel.on('afterOkClick', function(){
    
})

viewModel.on('afterOkClick', function(){
    
})

```






