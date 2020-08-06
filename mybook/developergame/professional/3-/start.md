
#### 设备分类，启用行删除按钮不显示

```
function (event) {
  var viewModel = this;
  //获取当前的model
  let gridModel = viewModel.getGridModel();
            //afterSetDataSource界面加载完成后，对数据进行修改
			gridModel.on('afterSetDataSource', () => {
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

#### 设备借用-保存前校验

```

function (event) {
  var viewModel = this;
  //设置保存前校验
  viewModel.on("beforeSave", function(args){
      var jieyongriqi = viewModel.get("jieyongriqi").getValue();
      var guihairiqi = viewModel.get("guihairiqi").getValue();
      const isAfterDate = (dateA, dateB) => dateA > dateB;
      if(!isAfterDate(guihairiqi, jieyongriqi)){
        cb.utils.alert("归还日期要大于借用日期")
        return false;
      }
  })
} 

```

#### 设备台账列表-删除前校验

```
function (event) {
  var viewModel = this;
  let gridModel = viewModel.getGridModel();
  const actionsStates = [];
  //删除前校验
  viewModel.on("beforeBatchdelete", function(args){
      const rows = gridModel.getSelectedRows();
      rows.forEach(data => {
				if(data.shebeizhuangtai==1){
				  actionsStates.push("编码:"+data.code+"为在用设备不能删除");
				}
			});
			if(actionsStates.length>0){
        cb.utils.alert(actionsStates);
        actionsStates.splice(0,actionsStates.length);
        return false;
      }
  })
}

```
