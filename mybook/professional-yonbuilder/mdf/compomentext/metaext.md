## 容器组件扩展

### 组件库

[组件库](http://bee.tinper.org/tinper-bee/)
- MDF对tinper-bee 进行了封装
- 可以查看基本的样式，然后进行修改使用


### 以基础组件库的步骤条 Step为例

#### 文档地址

- [基础组件库-步骤条Step](http://bee.tinper.org/tinper-bee/bee-step)
- 可以参考基础的实现效果，来写自己的代码。（实际有差异）

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/compomentext/images/13.png"/>
</div>
<p align="center">图 1</p>


#### 目标

封装一个步骤条Step，可以在页面设计器进行配置步骤内容，并实现根据实体元数据设置当前步骤


#### 创建文件

src/web/common/extends/meta/  下创建  mySteps.jsx

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/compomentext/images/14.png"/>
</div>
<p align="center">图 2</p>

#### 步骤条Step点击查看源码

复制粘贴到mySteps.jsx中

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/compomentext/images/15.png"/>
</div>
<p align="center">图 3</p>

```
/**
*
* @title 基础 Step
* @description current 标记当前进行哪一步
*
*/

import React, { Component } from 'react';
import { Step } from 'tinper-bee';


class Demo1 extends Component {
  render () {
      return (
          <Step.Steps current={1}>
            <Step title="已完成" description="这是一段描述" />
            <Step title="进行中" description="这是一段描述" />
            <Step title="未开始" description="这是一段描述" />
          </Step.Steps>
      )
  }
}

export default Demo1;

```

#### 修改代码

- 修改名称为mytag
- 修改引入的组件为MDF的

```
/**
*
* @title 基础 Step
* @description current 标记当前进行哪一步
*
*/

import React, { Component } from 'react';
//可以按Ctrl点击进入查看antd中注册的组件
//Ctrl点击进入查看Steps传参及使用的变化
import { Steps  } from 'antd';


class mySteps extends Component {
  render () {
      return (
          <Steps current={1}>
            <Steps.Step title="已完成" description="这是一段描述" />
            <Steps.Step title="进行中" description="这是一段描述" />
            <Steps.Step title="未开始" description="这是一段描述" />
          </Steps>
      )
  }
}

export default mySteps;

```

### 注册

src/web/common/extends/meta/index.jsx

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/compomentext/images/16.png"/>
</div>
<p align="center">图 4</p>

```
export mySteps from './mySteps';

```

### 使用

在页面上新建一个表单容器，然后更改其cControlType属性的值为：mySteps

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/compomentext/images/17.png"/>
</div>
<p align="center">图 5</p>


### 效果展示

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/compomentext/images/18.png"/>
</div>
<p align="center">图 6</p>


### 代码优化

可以在页面设计器进行配置步骤内容，并实现根据实体元数据设置当前步骤

```

/**
*
* @title 自定义图标
* @description
*
*/
import React, { Component } from 'react';
import { Steps  } from 'antd';



class mySteps extends Component {

  constructor(props) {
    super(props);
    //从props中获取meta,viewModel属性
    var {meta,viewModel} = this.props;
    this.state = {
      controls : meta.controls,
      rowData:viewModel.getParams()['billData']
    }
  }
  
  //根据容器内的控件的cShowCaption，describe来显示标题和描述
  renderContentNode(){
    var items = [];
    this.state.controls.map((item) => {
      items.push(<Steps.Step  title={item.cShowCaption} description={item.describe}/>);
    })
    return items;
  }

  render () {
    const contentNode = this.renderContentNode();
    //依据页面参数stepCurrentState判断走到哪一步
    const currentState = this.state.rowData.stepCurrentState;
      return (
          <Steps current={currentState?currentState:0}>
            {contentNode}
          </Steps>
      )
  }
}

export default mySteps;

```

#### 元数据修改

实体中增加stepCurrentState字段，用来存储当前步骤条在第几步

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/compomentext/images/19.png"/>
</div>
<p align="center">图 7</p>

- stepCurrentState字段在UI元数据（页面）中配置显示
- mySteps容器中新增基础文本控件。修改cShowCaption为要显示的title.
- 基础文本控件中新增属性describe，并添加描述

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/compomentext/images/20.png"/>
</div>
<p align="center">图 8</p>

#### 效果展示

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/compomentext/images/21.png"/>
</div>
<p align="center">图 9</p>



