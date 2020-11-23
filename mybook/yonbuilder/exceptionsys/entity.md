## 元数据

#### 实体

###### 异常情况记录

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="500px" colspan="4">异常情况记录</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="4">abnormalevent</td>
    </tr>
    <tr align="center">
        <td>父实体：</td>
        <td colspan="4"></td>
    </tr>
    <tr align="center">
        <td>引用接口：</td>
        <td colspan="4">自动编码/主组织</td>
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
        <td>title</td>
        <td>标题</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>importance</td>
        <td>重要程度</td>
        <td>单选</td>
        <td>重要程度</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>info_level</td>
        <td>信息登记</td>
        <td>单选</td>
        <td>信息登记</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>dealing_situation</td>
        <td>处理情况</td>
        <td>单选</td>
        <td>处理情况</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>look_situation</td>
        <td>查看情况</td>
        <td>单选</td>
        <td>查看情况</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>look_num</td>
        <td>查看次数</td>
        <td>整数</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>reponse_num</td>
        <td>回复次数</td>
        <td>整数</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>content</td>
        <td>问题内容</td>
        <td>大文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>StaffNew</td>
        <td>员工</td>
        <td>单元引用</td>
        <td>员工</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>files</td>
        <td>附件</td>
        <td>附件</td>
        <td></td>
    </tr> 
    <tr align="center">
        <td></td>
        <td>pictures</td>
        <td>图片</td>
        <td>图片</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>top</td>
        <td>置顶</td>
        <td>整数</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>invalid</td>
        <td>是否作废</td>
        <td>单选</td>
        <td>是否作废</td>
    </tr>   
</table>


###### 异常回复

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="500px" colspan="4">异常回复</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="4">reponse</td>
    </tr>
    <tr align="center">
        <td>父实体：</td>
        <td colspan="4">异常情况记录</td>
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
        <td>content</td>
        <td>回复内容</td>
        <td>大文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>reponsetype</td>
        <td>回复类型</td>
        <td>单选</td>
        <td>回复类型</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>dealing_situation</td>
        <td>处理状态</td>
        <td>单选</td>
        <td>处理状态</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>files</td>
        <td>附件</td>
        <td>附件</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>filesexplain</td>
        <td>附件说明</td>
        <td>附件说明</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>StaffNew</td>
        <td>员工</td>
        <td>单选引用</td>
        <td>员工</td>
    </tr> 
</table>


###### 大区

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="500px" colspan="4">大区</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="4">area</td>
    </tr>
    <tr align="center">
        <td>父实体：</td>
        <td colspan="4"></td>
    </tr>
    <tr align="center">
        <td>引用接口：</td>
        <td colspan="4">自动编码</td>
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
        <td>名称</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>StaffNew</td>
        <td>负责人</td>
        <td>单选引用</td>
        <td>员工</td>
    </tr> 
</table>


###### 门店

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="500px" colspan="4">门店</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="4">stores</td>
    </tr>
    <tr align="center">
        <td>父实体：</td>
        <td colspan="4"></td>
    </tr>
    <tr align="center">
        <td>引用接口：</td>
        <td colspan="4">自动编码</td>
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
        <td>名称</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>StaffNew</td>
        <td>负责人</td>
        <td>单选引用</td>
        <td>员工</td>
    </tr> 
    <tr align="center">
        <td></td>
        <td>area</td>
        <td>负责人</td>
        <td>单选引用</td>
        <td>大区</td>
    </tr> 
</table>

###### 店员

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="500px" colspan="4">店员</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="4">employee</td>
    </tr>
    <tr align="center">
        <td>父实体：</td>
        <td colspan="4">门店</td>
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
        <td>StaffNew</td>
        <td>员工</td>
        <td>单选引用</td>
        <td>员工</td>
    </tr> 
</table>



