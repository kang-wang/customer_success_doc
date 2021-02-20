## 扩展整个页面

非元数据开发的页面我们在src/web/common/extends/portal下编写，portal下的页面都当做一个单独的页面进行访问。

- 备注：具体示例待更新

### 创建页面
 
我们在portal下增加个hello.jsx，在里面输入hello, world!

```

import React from 'react';
export default class Welcome extends React.Component{  
    render(){
        return (<div> hello</div>)
    }
}

```

### 注册页面

src/web/common/extends/portal下的index页面，将新写的组件注入进去

```
import Hello from './hello'
    
export default {
     hello: { default: Hello }
}

```


### 使用

访问节点 /platform/hello,就可以访问到刚刚编写的页面组件.这里的hello，就是刚刚注入的Hello组件对应的keys字段。

访问：http://local.yonyoucloud.com:3003/platform/hello


<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/ext/images/7.png"/>
</div>
<p align="center">图 1</p>









