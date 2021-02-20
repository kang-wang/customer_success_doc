## 基础组件扩展

### 基础组件库

[基础组件库](http://bee.tinper.org/tinper-bee/)
- MDF对tinper-bee 进行了封装

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/compomentext/images/5.png"/>
</div>
<p align="center">图 1</p>

- 如何引用组件?

例如
```
import { Tag } from 'antd';

```

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/compomentext/images/6.png"/>
</div>
<p align="center">图 2</p>


### 以基础组件库的标签为例

#### 文档地址

- [基础组件库-标签](http://bee.tinper.org/tinper-bee/bee-tag)
- 可以参考基础的实现效果，来写自己的代码。（实际有差异）

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/compomentext/images/2.png"/>
</div>
<p align="center">图 2</p>


#### 目标

设置一个标签控件，并使用

#### 创建文件

src/web/common/extends/basic/  下创建  mytag.jsx

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/compomentext/images/3.png"/>
</div>
<p align="center">图 3</p>

#### 标签库点击查看源码

复制粘贴到mytag.jsx中

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/compomentext/images/4.png"/>
</div>
<p align="center">图 4</p>

```
/**
*
* @title 语意色标签
* @description 表示提示信息的标签。
* 
*/
import React, { Component } from 'react';
import { Tag } from 'tinper-bee';

class Demo2 extends Component {
    render () { 
        return (
            <div className="demoPadding">
                <Tag colors="success">success</Tag>
                <Tag colors="warning">warning</Tag>
                <Tag colors="danger">danger</Tag>
                <Tag colors="info">info</Tag>
             </div>
        )
    }
}

export default Demo2;
```

#### 修改代码

- 修改名称为mytag
- 修改引入的组件为MDF的
- 增加构造方法 props可以获取到组件的属性及viewModel

```

/**
*
* @title 语意色标签
* @description 表示提示信息的标签。
* 
*/
import React, { Component } from 'react';
import { Tag } from 'antd';

class mytag extends Component {

    constructor(props) {
        super(props);
    }

    render () {
        let {cCaption} = this.props 
        return (
            <Tag color="yellow">{cCaption}</Tag>
        )
    }
}

export default mytag;

```

#### 分析

会发现

```
<Tag color="yellow">{cCaption}</Tag>
```

传参有变化，这就是MDF封装导致的差异。需要看源码来调整

- 查看组件代码，按Ctrl+鼠标点击即可穿透查看

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/compomentext/images/7.png"/>
</div>
<p align="center">图 5</p>

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/compomentext/images/8.png"/>
</div>
<p align="center">图 6</p>

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/compomentext/images/9.png"/>
</div>
<p align="center">图 7</p>


### 注册

src/web/common/extends/basic/index.jsx

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/compomentext/images/10.png"/>
</div>
<p align="center">图 8</p>

```
export mytag from './mytag';
```

### 使用

修改控件的cControlType属性的值为：mytag

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/compomentext/images/11.png"/>
</div>
<p align="center">图 9</p>


### 效果展示

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/compomentext/images/12.png"/>
</div>
<p align="center">图 10</p>










