## 创建应用

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/1-/images/2.png"/>
</div>
<p align="center">图 1</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/1-/images/1.png"/>
</div>
<p align="center">图 2</p>

## 创建元数据

### 枚举

#### 重要程度

操作 | 描述 | |
---|---|---
名称 | 重要程度 |
编码 | importance |
类型 | 字符 |
枚举内容 | 枚举值 | 名称
| 1 | 紧急事件 
| 2 | 重要事件 
| 3 | 一般事件

#### 事项类型

操作 | 描述 ||
---|---|---
名称 | 事项类型 |
编码 | matter_type |
类型 | 字符 |
枚举内容 | 枚举值 | 名称 
| 1| 执法部门检查   
|2 | 人员情况 
| 3| 员工状态 

#### 查看情况

操作 | 描述 | |
---|---|---
名称 | 事项类型 |
编码 | look_situation |
类型 | 字符 |
枚举内容 | 枚举值 | 名称 
| 1| 未查看
| 2| 已查看


### 实体

#### 异常记录

操作 | 描述 | | | ||
---|---|---|---|---|---
名称 | 异常记录 |  |  |  |
编码 | abnormalevent |  |  |  |
父实体 |  |  |  |  |
引用接口 | 自动编码 |  |  |  |
|属性 | 编码 | 名称 | 类型 | 引用 
| | title| 标题 | 文本 |   
| |importance | 重要程度 | 单选 | 重要程度  
| | look_situation| 查看情况 | 单选 |  查看情况
| | look_num| 查看次数 | 整数 |  
| | reponse_num| 回复次数 | 整数 |  
| |matter_type | 事项类型 | 单选 | 事项类型 
| |content | 问题内容 | 大文本 |  
| |StaffNew | 创建人 |  单选引用| 员工
| | files| 附件 | 附件 |  
| | pictures| 图片 | 图片 |  


#### 异常记录回复

操作 | 描述 | | | ||
---|---|---|---|---|---
名称 | 异常记录回复 |  |  |  |
编码 | reponse |  |  |  |
父实体 | 异常记录 |  |  |  |
引用接口 |  |  |  |  |
|属性 | 编码 | 名称 | 类型 | 引用 
| | content| 回复内容 |  |
| |files | 附件 | 附件 |
| | filesexplain| 附件说明 | 大文本 |
| | StaffNew| 员工 | 单选引用 | 员工 


#### 集团

操作 | 描述 | | | ||
---|---|---|---|---|---
名称 | 集团 |  |  |  |
编码 | org |  |  |  |
父实体 |  |  |  |  |
引用接口 | 自动编码 |  |  |  |
|属性 | 编码 | 名称 | 类型 | 引用 
| | name | 名称 | 大文本 |  
| | StaffNew | 负责人 | 单选引用 | 员工  

#### 大区

操作 | 描述 | | | ||
---|---|---|---|---|---
名称 | 大区 |  |  |  |
编码 | area |  |  |  |
父实体 |  |  |  |  |
引用接口 | 自动编码 |  |  |  |
|属性 | 编码 | 名称 | 类型 | 引用 
| | name | 名称 | 大文本 |   
| | StaffNew | 负责人 | 单选引用 | 员工  

#### 门店

操作 | 描述 | | | ||
---|---|---|---|---|---
名称 | 门店 |  |  |  |
编码 | store |  |  |  |
父实体 |  |  |  |  |
引用接口 | 自动编码 |  |  |  
|属性 | 编码 | 名称 | 类型 | 引用 
| | name | 名称 | 大文本 |   
| | StaffNew | 负责人 | 单选引用 | 员工 


#### 店员

操作 | 描述 | | | ||
---|---|---|---|---|---
名称 | 门店 |  |  |  |
编码 | employee |  |  |  |
父实体 |  |  |  |  |
引用接口 | 自动编码 |  |  |  |
|属性 | 编码 | 名称 | 类型 | 引用  
| | StaffNew | 负责人 | 单选引用 | 员工 


## 页面建模

#### 新建【集团】【大区】行编辑表

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/1-/images/3.png"/>
</div>
<p align="center">图 3</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/1-/images/4.png"/>
</div>
<p align="center">图 4</p>


#### 新建【大区】参照

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/1-/images/5.png"/>
</div>
<p align="center">图 5</p>

#### 新建【门店】【异常记录】一主多子页面

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/1-/images/6.png"/>
</div>
<p align="center">图 6</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/1-/images/7.png"/>
</div>
<p align="center">图 7</p>

设置门店子表允许为空

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/1-/images/12.png"/>
</div>
<p align="center">图 8</p>



### 录入测试数据

#### 集团

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/1-/images/8.png"/>
</div>
<p align="center">图 9</p>

#### 大区

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/1-/images/9.png"/>
</div>
<p align="center">图 10</p>

#### 门店

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/1-/images/11.png"/>
</div>
<p align="center">图 11</p>

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/1-/images/10.png"/>
</div>
<p align="center">图 12</p>












