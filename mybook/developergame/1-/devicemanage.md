# 设备管理

## 需求概述

包括设备从登记开始,
设备使用(设备借用、携带外出、设备移交)、设备变更、设备维护等基础的设备管理业务，也包括设备折旧、使用费计提

## 准备资料

#### 枚举

###### 设备状态

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="200px">名称：</td>
        <td width="300px" colspan="2">设备状态</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="2">emst</td>
    </tr>
    <tr align="center">
        <td>类型：</td>
        <td colspan="2">字符</td>
    </tr>
    <tr align="center">
        <td>枚举内容：</td>
        <td>枚举值</td>
        <td>名称</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>1</td>
        <td>在用</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>2</td>
        <td>闲置</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>3</td>
        <td>维修</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>4</td>
        <td>借用</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>5</td>
        <td>外带</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>6</td>
        <td>报废</td>
    </tr>
</table>

###### 维护方式

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="200px">名称：</td>
        <td width="300px" colspan="2">维护方式</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="2">whtype</td>
    </tr>
    <tr align="center">
        <td>类型：</td>
        <td colspan="2">字符</td>
    </tr>
    <tr align="center">
        <td>枚举内容：</td>
        <td>枚举值</td>
        <td>名称</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>1</td>
        <td>人工巡检</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>2</td>
        <td>自动监测</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>3</td>
        <td>无</td>
    </tr>
</table>

#### 实体

###### 设备大类

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="500px" colspan="4">设备大类</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="4">equipmentcategory</td>
    </tr>
    <tr align="center">
        <td>父实体：</td>
        <td colspan="4"></td>
    </tr>
    <tr align="center">
        <td>引用接口：</td>
        <td colspan="4"></td>
    </tr>
    <tr align="center">
        <td>属性：</td>
        <td>编码</td>
        <td>名称</td>
        <td>类型</td>
        <td>引用</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>name</td>
        <td>类型名称</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>esort</td>
        <td>序号</td>
        <td>文本</td>
        <td></td>
    </tr>
</table>


###### 设备分类

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="500px" colspan="4">设备分类</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="4">equipmentclass</td>
    </tr>
    <tr align="center">
        <td>父实体：</td>
        <td colspan="4"></td>
    </tr>
    <tr align="center">
        <td>引用接口：</td>
        <td colspan="4">档案状态</td>
    </tr>
    <tr align="center">
        <td>属性：</td>
        <td>编码</td>
        <td>名称</td>
        <td>类型</td>
        <td>引用</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>name</td>
        <td>分类名称</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>csort</td>
        <td>排序</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>sbdl</td>
        <td>设备大类</td>
        <td>单选引用</td>
        <td>设备大类</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>shebeidaleiid</td>
        <td>设备大类id</td>
        <td>文本</td>
        <td></td>
    </tr>
</table>


###### 设备卡片

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="500px" colspan="4">设备卡片</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="4">emcard</td>
    </tr>
    <tr align="center">
        <td>父实体：</td>
        <td colspan="4"></td>
    </tr>
    <tr align="center">
        <td>引用接口：</td>
        <td colspan="4">审批/业务流/自动编码</td>
    </tr>
    <tr align="center">
        <td>属性：</td>
        <td>编码</td>
        <td>名称</td>
        <td>类型</td>
        <td>引用</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>name</td>
        <td>设备名称</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>sbdl</td>
        <td>设备大类</td>
        <td>单选引用</td>
        <td>设备大类</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>sbfl</td>
        <td>设备分类</td>
        <td>单选引用</td>
        <td>设备分类</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>zerenren</td>
        <td>责任人</td>
        <td>单选引用</td>
        <td>员工</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>zerenbumen</td>
        <td>责任部门</td>
        <td>单选引用</td>
        <td>行政部门</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>shiyongren</td>
        <td>使用人</td>
        <td>单选引用</td>
        <td>员工</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>yongtu</td>
        <td>用途</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>yongtu</td>
        <td>用途</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>shiyongqingkuang</td>
        <td>使用情况</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>shebeixinghao</td>
        <td>设备型号</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>shebeiguige</td>
        <td>设备规格</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>chuchangbianhao</td>
        <td>出厂编号</td>
        <td>文本</td>
        <td></td>
    </tr><tr align="center">
        <td></td>
        <td>chuchangriqi</td>
        <td>出厂日期</td>
        <td>日期</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>shebeizhuangtai</td>
        <td>设备状态</td>
        <td>单选</td>
        <td>设备状态</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>MACdizhi</td>
        <td>MAC地址</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>IPdizhi</td>
        <td>IP地址</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>caozuoxitong</td>
        <td>操作系统名称</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>xitongriqi</td>
        <td>系统日期</td>
        <td>日期</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>weihufangshi</td>
        <td>维护方式</td>
        <td>单选</td>
        <td>维护方式</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>zhihangjihua</td>
        <td>执行计划</td>
        <td>文本</td>
        <td></td>
    </tr>
</table>

###### 设备借用

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="500px" colspan="4">设备借用</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="4">sbjy</td>
    </tr>
    <tr align="center">
        <td>父实体：</td>
        <td colspan="4"></td>
    </tr>
    <tr align="center">
        <td>引用接口：</td>
        <td colspan="4">审批/业务流</td>
    </tr>
    <tr align="center">
        <td>属性：</td>
        <td>编码</td>
        <td>名称</td>
        <td>类型</td>
        <td>引用</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>jieyongren</td>
        <td>借用人</td>
        <td>单选引用</td>
        <td>员工</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>jieyongriqi</td>
        <td>借用日期</td>
        <td>日期</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>guihairiqi</td>
        <td>归还日期</td>
        <td>日期</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>emcard3</td>
        <td>设备卡片</td>
        <td>单选引用</td>
        <td>设备卡片</td>
    </tr>
</table>


## 操作流程

1. 新建单卡【设备大类】,勾选【生成参照】
2. 发布参照
3. 新建单卡【设备分类】,勾选【生成参照】
4. 发布参照
5. 新建单卡【设备台账】,勾选【生成参照】
6. 调整布局样式
7. 更改【设备台账参照】名为：【可借出设备】
8. 新建单片【设备借用】
9. 调整【设备借用卡片】中参照【设备卡片】过滤事项：设备状态为，闲置
10. 验证保存一个借用单据

## 预告

明天会在此项目的基础上
1. 配置一个借出设备审批流
2. 创建设备巡检相关，配置一个业务流
