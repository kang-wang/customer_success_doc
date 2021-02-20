## 单据扩展

### 建议

单据扩展这部分功能完全可以被函数替代，请优先使用函数。

### 启用单据扩展

脚手架默认不启用单据扩展，推荐使用函数。如果需要使用，请参照以下配置

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/ext/images/1.png"/>
</div>
<p align="center">图 1</p>

```

const businessContext = require.context('business');

```

### 单据扩展命名

预览页面

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/ext/images/2.png"/>
</div>
<p align="center">图 2</p>

扩展脚本名称

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/ext/images/3.png"/>
</div>
<p align="center">图 3</p>


### 创建文件

src/businesss/   目录下创建

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/ext/images/4.png"/>
</div>
<p align="center">图 4</p>


### 代码

#### 基础代码

GT5439AT29_dfbc4e1fList_VM_Extend 为查看的函数名。主意一共有三处需要修改
```
cb.define(['common/common_VM.Extend.js'], function (common) {
    let GT5439AT29_dfbc4e1fList_VM_Extend = {
      doAction: function (name, viewmodel) {
        if (this[name])
            this[name](viewmodel);
      },
      init: function (viewmodel) {
        let self = this;
      }
    }
    try {
      module.exports = GT5439AT29_dfbc4e1fList_VM_Extend;
    } catch (error) {
  
    }
    return GT5439AT29_dfbc4e1fList_VM_Extend;
  });
```

#### 扩展代码

扩展代码一般写在init中，使用mdf的事件即可。
例如列表过滤


```
cb.define(['common/common_VM.Extend.js'], function (common) {
    let GT5439AT29_dfbc4e1fList_VM_Extend = {
      doAction: function (name, viewmodel) {
        if (this[name])
            this[name](viewmodel);
      },
      init: function (viewmodel) {
        let self = this;
        viewmodel.on('beforeSearch',function(args){
            args.isExtend = true;
            var commonVOs = args.params.condition.commonVOs;  //通用检查查询条件
            commonVOs.push({
                itemName:'new1',
                op:'eq',
                value1:'11'
            });
            debugger;
        })
      }
    }
    try {
      module.exports = GT5439AT29_dfbc4e1fList_VM_Extend;
    } catch (error) {
  
    }
    return GT5439AT29_dfbc4e1fList_VM_Extend;
});

```









