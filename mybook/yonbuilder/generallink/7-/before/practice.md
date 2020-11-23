## 常见事件使用

初始化函数常见事件

## 列表界面常用事件

```

beforeSearch       //列表查询前事件
beforeSetDataSource   //设置数据源前的事件
afterSetDataSource    //设置数据源后的事件

```

#### 示例


#### beforeSearch

示例提供的是列表界面查询过滤
过滤条件通过调用api函数获取到
```javascript

viewModel.on('beforeSearch',function(args){
      //需要获取当前人的身份信息，确定默认的查询条件
      var promise = new cb.promise();
      setTimeout(function() {
        cb.rest.invokeFunction("2abae82cef154bd194d7069135011395", {},
      function(err, res) {
        if(err!=null){
          cb.utils.alert('查询数据异常');
          permissions = [];
          return false;
        }else{
          args.isExtend = true;
          //请求数据的条件，获取统计信息的时候需要用到
          reqCondition= args.params.condition;
          commonVOs = args.params.condition.commonVOs;
          if(undefined==permissions){
            //设置一个不可能查询出数据的条件
            cb.utils.alert('查询数据异常--获取人员失败');
              commonVOs.push({
                itemName:'id',
                op:'eq',
                value1:''
              });
          }else{
			var permissions = res.res;
			var alldata = res.allData;
            if(undefined==alldata){
              if(permissions.length>0){
                var conditions = args.params.condition;
                conditions.simpleVOs=
                  [{
                    "logicOp": "and",
                    "conditions": [{
                        "logicOp": "or",
                        "conditions": [{
                          "field": "matter_type_m",
                          "op": "eq",
                          "value1": '3'
                          },
                          {
                          "field": "StaffNew",
                          "op": "in",
                          "value1": permissions
                        }]
                  }]
                }];
            }else{
              commonVOs.push({
                itemName:'matter_type_m',
                op:'eq',
                value1:'3'
              });
            }
          }
        }
        promise.resolve();
        }
      })
      }, 10);
      return promise;
  })

```

#### beforeSetDataSource

```javascript

let gridModel = viewModel.getGridModel();
gridModel.on('beforeSetDataSource', (data) => {
    var change_data = JSON.parse(JSON.stringify(data));
});

```


#### afterSetDataSource

```javascript

let gridModel = viewModel.getGridModel();
gridModel.on('afterSetDataSource', (data) => {
    var change_data = JSON.parse(JSON.stringify(data));
});

```

## 卡片界面常用事件


```

afterLoadData       //数据加载完成后事件

```

#### afterLoadData

```javascript

viewModel.on('afterLoadData', function () {
    var id = viewModel.get("id").getValue();
});

```



