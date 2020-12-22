## 按钮权限

### 功能目标

- 异常记录列表表格行按钮控制：集团人员有所有按钮权限，创建人有编辑、删除权限。其他人没有编辑、删除权限

### 功能点

```

function (event) {
  var viewModel = this;
  //获取当前的model
  let gridModel = viewModel.getGridModel();
  //afterSetDataSource界面加载完成后，对数据进行修改
  gridModel.on('afterStateRuleRunGridActionStates', () => {
  //获取列表所有数据
  const rows = gridModel.getRows();
  //从缓存区获取按钮
  const actions = gridModel.getCache('actions');
  if (!actions) return;
  const actionsStates = [];
  rows.forEach(data => {
    const actionState = {};
    actions.forEach(action => {
    //设置按钮可用不可用
    actionState[action.cItemName] = { visible: true };
    if(action.cItemName == 'btnDelete'){
        if(data.enable==1){
            actionState[action.cItemName] = { visible: false };
        }
    }
	});
	actionsStates.push(actionState);
  });
  gridModel.setActionsState(actionsStates);
  });
}
```

### 功能实现

#### 后端API函数

使用【设置默认创建者】API函数即可

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/53.png"/>
</div>
<p align="center">图 1</p>


#### 前端函数

请求api函数获取当前员工信息

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/54.png"/>
</div>
<p align="center">图 2</p>

异常记录列表初始化函数新增内容

```
//设置表格行按钮
  gridModel.on('afterStateRuleRunGridActionStates', () => {
    //说明是集团人员,有所有权限直接return
    if(undefined!=alldata){
      return;
    }
    var promise = new cb.promise();
    //
    cb.rest.invokeFunction("7e0dbb242a98483181c2ef91e041c2d8", {},
    function(err, res) {
      if(err!=null){
        cb.utils.alert("查询员工信息报错");
        return false;
      }else{
        //获取列表所有数据
        const rows = gridModel.getRows();
        //从缓存区获取按钮
        const actions = gridModel.getCache('actions');
        if (!actions) return;
        const actionsStates = [];
        rows.forEach(data => {
          const actionState = {};
          actions.forEach(action => {
            //设置按钮可用不可用
            actionState[action.cItemName] = { visible: true };
            if(action.cItemName == 'btnEdit'||action.cItemName == 'btnDelete'){
              if(data.StaffNew!=res.userid){
                actionState[action.cItemName] = { visible: false };
            }
          }
	      });
	      actionsStates.push(actionState);
    });
    gridModel.setActionsState(actionsStates);
      }
      
    })
  });
```

### 测试

#### 集团

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/57.png"/>
</div>
<p align="center">图 3</p>


#### 其他

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/55.png"/>
</div>
<p align="center">图 4</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/3-/images/56.png"/>
</div>
<p align="center">图 5</p>




