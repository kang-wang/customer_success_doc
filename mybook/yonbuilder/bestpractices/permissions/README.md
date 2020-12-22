## 项目背景

一家KTV集团需要对其所有的KTV场所,进行异常情况的集中管控。
该集团的整体组织架构为：集团、大区、门店，三级关系。

## 场景分析

#### 权限管控

- 集团负责人可以查看所有的数据信息
- 大区负责人可以查看大区内所有门店的异常数据信息
- 门店负责人只能看到自己门店内发生的异常数据信息
- "员工状态"类事项不做权限控制，全平台都可以查看

<div align=center>
<img src="/mybook/yonbuilder/bestpractices/permissions/images/1.png"/>
</div>
<p align="center">图 1</p>

#### 查看记录

- 记录查看人员信息并可通过弹出模态框的方式获取到查看记录列表信息
- 当前人未查看的异常描述变为红色


#### 按钮权限

- 只有提交人可以修改\删除数据，其他人只能查看。没有权限的隐藏修改、删除按钮

## 功能清单

功能节点 | 实现方式
---|---
[数据权限](/mybook/yonbuilder/bestpractices/permissions/2-/queryfilter.md) | 列表过滤
[阅读记录(模态框)](/mybook/yonbuilder/bestpractices/permissions/3-/README.md)  | 模态框
[查看情况(样式扩展)](/mybook/yonbuilder/bestpractices/permissions/3-/update.md)  | CSS样式扩展
[按钮权限](/mybook/yonbuilder/bestpractices/permissions/3-/btnfilter.md)  | 表格按钮显示控制






