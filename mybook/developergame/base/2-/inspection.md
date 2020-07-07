# 设备巡检

## 需求概述

包括设备从登记开始,
设备使用(设备借用、携带外出、设备移交)、设备变更、设备纬护等基础的设备管理业务，也包括设备折旧、使用费计提


## 准备资料

#### 实体

###### 设备巡检

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="500px" colspan="4">设备巡检</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="4">ssbxj</td>
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
        <td>sbmc</td>
        <td>设备名称</td>
        <td>单选引用</td>
        <td>设备卡片</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>name</td>
        <td>巡检名</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>fuzeren</td>
        <td>负责人</td>
        <td>单选引用</td>
        <td>员工</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>xunjianyuan</td>
        <td>巡检员</td>
        <td>多选引用</td>
        <td>员工</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>shebeidingwei</td>
        <td>设备定位</td>
        <td>定位</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>dingweijingdu</td>
        <td>定位经度</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>dingweiweidu</td>
        <td>定位纬度</td>
        <td>文本</td>
        <td></td>
    </tr>
</table>

###### 巡检计划表

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="500px" colspan="4">巡检计划表</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="4">xjjhb</td>
    </tr>
    <tr align="center">
        <td>父实体：</td>
        <td colspan="4">设备巡检</td>
    </tr>
    <tr align="center">
        <td>引用接口：</td>
        <td colspan="4">业务流</td>
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
        <td>计划名称</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>kaishishijian</td>
        <td>开始时间</td>
        <td>时间</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>jieshushijian</td>
        <td>结束时间</td>
        <td>时间</td>
        <td></td>
    </tr>
</table>

###### 巡检执行

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="500px" colspan="4">巡检执行</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="4">xjzj</td>
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
        <td>ssbxj</td>
        <td>设备巡检</td>
        <td>单选引用</td>
        <td>设备巡检</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>shebeijingdu</td>
        <td>设备经度</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>shebeiweidu</td>
        <td>设备纬度</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>dangqianweizhi</td>
        <td>当前位置</td>
        <td>定位</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>dangqianjingdu</td>
        <td>当前经度</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>dangqianweidu</td>
        <td>当前纬度</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>xunjianyuan</td>
        <td>巡检员</td>
        <td>单选引用</td>
        <td>员工</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>zhihangren</td>
        <td>执行人</td>
        <td>单选引用</td>
        <td>员工</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>shebei</td>
        <td>设备</td>
        <td>单选引用</td>
        <td>设备卡片</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>xunjianming</td>
        <td>巡检名</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>jihuamingcheng</td>
        <td>计划名称</td>
        <td>文本</td>
        <td></td>
    </tr>
</table>

## 操作流程

1. 配置审批流

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="700px" colspan="3">设备借用</td>
    </tr>
    <tr align="center">
        <td>流程：</td>
        <td colspan="3"></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>流程一</td>
        <td colspan="2"></td>
    </tr>
    <tr align="center">
        <td></td>
        <td></td>
        <td>名称:</td>
        <td>确认</td>
    </tr>
    <tr align="center">
        <td></td>
        <td></td>
        <td>参与人:</td>
        <td>发起人</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>流程二</td>
        <td colspan="2"></td>
    </tr>
    <tr align="center">
        <td></td>
        <td></td>
        <td>名称:</td>
        <td>领导审批</td>
    </tr>
    <tr align="center">
        <td></td>
        <td></td>
        <td>参与人:</td>
        <td>发起人/制单人部门负责人（包含上级）</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>流程三</td>
        <td colspan="2"></td>
    </tr>
    <tr align="center">
        <td></td>
        <td></td>
        <td>名称:</td>
        <td>设备管理员</td>
    </tr>
    <tr align="center">
        <td></td>
        <td></td>
        <td>参与人:</td>
        <td>发起人/选择一个用户</td>
    </tr>
    <tr align="center">
        <td>属性设置：</td>
        <td colspan="3">流程结束后允许撤回</td>
    </tr>
    <tr align="center">
        <td>流程字段权限：</td>
        <td colspan="3">流程一，修改人改为可编辑</td>
    </tr>
</table>

2. 验证审批流
3. 新建页面一主多子【设备巡检计划】,勾选【生成参照】
4. 调整页面主子单据布局
5. 调整参照布局并发布
6. 新建单卡【巡检执行】
7. 调整【巡检执行】中参照【设备名称】过滤事项：设备状态为，在用
8. 配置业务流
<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="700px" colspan="5">设备巡检</td>
    </tr>
    <tr align="center">
        <td>推送：</td>
        <td colspan="5">设备巡检推送巡检执行</td>
    </tr>
    <tr align="center">
        <td>规则：</td>
        <td>基本信息:</td>
        <td colspan="2"></td>
        <td colspan="2"></td>
    </tr>
    <tr align="center">
        <td></td>
        <td></td>
        <td colspan="2">规则名称:</td>
        <td colspan="2">巡检推计划</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>触发设置:</td>
        <td colspan="2"></td>
        <td colspan="2"></td>
    </tr>
    <tr align="center">
        <td></td>
        <td></td>
        <td colspan="2">推送时机:</td>
        <td colspan="2">手工触发</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>生单方式:</td>
        <td colspan="2"></td>
        <td colspan="2"></td>
    </tr>
    <tr align="center">
        <td></td>
        <td></td>
        <td colspan="2">推送方式:</td>
        <td colspan="2">新增单据</td>
    </tr>
    <tr align="center">
        <td></td>
        <td></td>
        <td colspan="2">新增单据状态:</td>
        <td colspan="2">开立态</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>转换规则:</td>
        <td colspan="2"></td>
        <td colspan="2"></td>
    </tr>
    <tr align="center">
        <td></td>
        <td></td>
        <td>目标字段</td>
        <td>关联选择</td>
        <td>来源单据</td>
        <td>来源字段</td>
    </tr>
    <tr align="center">
        <td></td>
        <td></td>
        <td>当前位置</td>
        <td>简单映射</td>
        <td>设备巡检</td>
        <td>设备定位</td>
    </tr>
    <tr align="center">
        <td></td>
        <td></td>
        <td>计划名称</td>
        <td>简单映射</td>
        <td>巡检计划表</td>
        <td>计划名称</td>
    </tr>
    <tr align="center">
        <td></td>
        <td></td>
        <td>巡检名</td>
        <td>简单映射</td>
        <td>设备巡检</td>
        <td>巡检名</td>
    </tr>
    <tr align="center">
        <td></td>
        <td></td>
        <td>巡检员</td>
        <td>简单映射</td>
        <td>设备巡检</td>
        <td>巡检员</td>
    </tr>
</table>

9. 验证业务流

## 预告

明天会在此项目的基础上
1. 函数扩展