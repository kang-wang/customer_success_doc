
#### 实体

###### 交通费报销单

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="500px" colspan="4">交通费报销单</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="4">tpt_expense</td>
    </tr>
    <tr align="center">
        <td>父实体：</td>
        <td colspan="4"></td>
    </tr>
    <tr align="center">
        <td>引用接口：</td>
        <td colspan="4">审批/自动编码/主组织</td>
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
        <td>date</td>
        <td>单据日期</td>
        <td>日期</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>person</td>
        <td>报销人</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>dept</td>
        <td>费用承担部门</td>
        <td>文本</td>
        <td></td>
    </tr> 
    <tr align="center">
        <td></td>
        <td>money</td>
        <td>报销金额</td>
        <td>数值</td>
        <td></td>
    </tr>   
</table>


###### 交通费报销单子表

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="500px" colspan="4">交通费报销单子表</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="4">tpt_expense_ch</td>
    </tr>
    <tr align="center">
        <td>父实体：</td>
        <td colspan="4">交通费报销单</td>
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
        <td>date</td>
        <td>日期</td>
        <td>日期</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>money</td>
        <td>报销金额</td>
        <td>数值</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>beginaddress</td>
        <td>出发地点</td>
        <td>文本</td>
        <td></td>
    </tr> 
    <tr align="center">
        <td></td>
        <td>endaddress</td>
        <td>到达地点</td>
        <td>文本</td>
        <td></td>
    </tr>   
</table>