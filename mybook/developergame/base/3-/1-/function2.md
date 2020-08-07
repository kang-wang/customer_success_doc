# 常用函数

## 页面初始化->设置默认值（前端函数）

```
function (event) {
  viewModel.get('userid').setValue(newPseudoGuid());
  viewModel.get('startdate').setValue(formatDate(new Date()));
} 

```

## 值改变后事件->校验邮箱格式（前端函数）

```
function (event) {
  var viewModel = this;
  let email = viewModel.get('email').getValue();
  const validateEmail = str =>
    /^(([^<>()\[\]\.,;:\s@"]+(\.[^<>()\[\]\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/.test(str);
  // validateEmail(mymail@gmail.com) -> true
  if(!validateEmail(email)){
    cb.utils.alert('邮箱格式错误');
  }
} 

```

## 值改变后事件->校验结束日期（前端函数）

```
function (event) {
  var viewModel = this;
  var enddate = viewModel.get('enddate').getValue();
  var startdate = viewModel.get('startdate').getValue();
  const isAfterDate = (dateA, dateB) => dateA > dateB;
  if(!isAfterDate(enddate, startdate)) {
    cb.utils.alert('结束日期必须大于开始日期');
  }
}
```


## 列表启用行删除按钮不显示

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

## 保存前校验

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

## 列表删除前校验

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

## 表格选中行

```
function (event) {
  var viewModel = this;
  var gridModel = viewModel.getGridModel();
  gridModel.on('afterSelect', function (data) {
		cb.utils.alert(data);
	});
}
```

## 卡片界面动态给表格设置默认值
```
function (event) {
  var viewModel = this;
  var gridModels = viewModel.getGridModels();
  var chList = viewModel.get("chList");
  chList.on('beforeInsertRow', function (data) {
					var vouchdate = this.getParent().get("new2").getValue();
					data.row['new2'] = vouchdate;
	});
}
```

## 卡片界面根据页面状态按钮控制显示
```
function (event) {
  var viewModel = this;
  viewModel.on("modeChange",function (data) {
	        if(data == "add"){
	          	viewModel.get("button24rj").setVisible(true);
	        }else{
	        	  viewModel.get("button24rj").setVisible(false);
	        }
	  	});
}
```

## 初始化自定义按钮绑定点击事件

```
function (event) {
  var viewModel = this;
  viewModel.get('button5ad').on('click', function () {
    var rows = viewModel.getGridModel().getSelectedRows();
    console.log(rows);
  })
}
```

## 表格自定义按钮获取选中行数据
```
function (event) {
  var viewModel = this;
  viewModel.get('button5vf').on('click', function (args) {
    var currentRow = viewModel.getGridModel().getRow(args.index);
  })
}
```

## 卡片界面枚举清空及设置默认值

```
  //ListModel方法及事件
   var sexModel=viewModel.get("sex");  //获取ListModel
   
   sexModel.clear();//ListModel清空方法
   
   sexModel.setValue(2); //ListModel设值
```

## 设置参照过滤

```
    //ReferModel方法及事件
   var nationModel=viewModel.get("nation_name");  //获取ReferModel
   var nationFiter = { 
     "isExtend": true,
       simpleVOs: []
         };
    nationFiter.simpleVOs.push({
       field: 'name',
       op: 'eq',
       value1: '汉族'
    });
    nationModel.setFilter(nationFiter);//设置过滤
```

## 设置列表查询过滤

```
function (event) {
  var viewModel = this;
  viewModel.on('beforeSearch', function (args) {
        args.isExtend = true;
        var commonVOs = args.params.condition.commonVOs
        commonVOs.push({
            itemName: 'new2',
            op: 'like',
            value1: "11"
          });
        commonVOs.push({
            itemName: 'gender',
            op: 'eq',
            value1: "2"
          });
      });
}
```

## 删行前弹出确定框

```
function (event) {
  var viewModel = this;
  viewModel.on("beforeDeleteRow",function (args) {
	     var returnPromise = new cb.promise();
	          cb.utils.confirm('确定要停用吗？', function(){
	            //获取选中行
	            var data = viewModel.getGridModel().getRows()[args.data[0]];
	            return returnPromise.resolve();
	          },function (args) {
	            cb.utils.alert("点击了取消");
	            returnPromise.reject();
	          });
	          return returnPromise;
	 	});
}
```

## 联动动态控制组件是否可编辑

```
function (event) {
  var viewModel = this;
  var sexModel=viewModel.get("sex");  //获取ListModel
  sexModel.on('afterValueChange',function(data){
       if(data.value.value=="1"){
         let phoneModel=viewModel.get("phone"); //获取手机控件
         phoneModel.setVisible(true);
         gridModel.setReadOnly(false); //设置gridModel可编辑

       }
}
```

## 设置组件是否必输

```
function (event) {
  var viewModel = this;
  var param = viewModel.get("new1");
  param.setState("bIsNull",false);
  cb.utils.alert(param);
}
```

## 前端调用controller  ---针对专业版controller

```
function (event) {
  var viewModel = this;
  var proxy = cb.rest.DynamicProxy.create({
				settle: {
					url: 'report/list',
					method: 'POST'
				}
			});
			//传参
			var param = {
				key: "value",
			};
			proxy.settle(param, function(err, result) {
				if (err) {
					cb.utils.alert(err.message, 'error');
					return;
				}
				if (result != undefined) {
					//对结果进行处理
				}
			});
}
```
