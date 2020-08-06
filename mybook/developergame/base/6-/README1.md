#### 枚举

###### 逻辑判断

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="200px">名称：</td>
        <td width="300px" colspan="2">逻辑判断</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="2">boolean01</td>
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
        <td>是</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>2</td>
        <td>否</td>
    </tr>
</table>


#### 实体

###### 地区分类

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="500px" colspan="4">地区分类</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="4">area_type</td>
    </tr>
    <tr align="center">
        <td>父实体：</td>
        <td colspan="4"></td>
    </tr>
    <tr align="center">
        <td>引用接口：</td>
        <td colspan="4">树型结构/自动编码</td>
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
        <td>地区名称</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>mnemoniccode</td>
        <td>助记码</td>
        <td>文本</td>
        <td></td>
    </tr>
</table>


###### 客商档案

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="500px" colspan="4">客商档案</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="4">customer_doc</td>
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
        <td>客商名称</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>shortname</td>
        <td>客商简称</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>foreignname</td>
        <td>外文名称</td>
        <td>文本</td>
        <td></td>
    </tr> 
    <tr align="center">
        <td></td>
        <td>mnemoniccode</td>
        <td>助记码</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>isretail</td>
        <td>是否散户</td>
        <td>单选</td>
        <td>逻辑判断</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>ischannel</td>
        <td>是否渠道成员</td>
        <td>单选</td>
        <td>逻辑判断</td>
    </tr> 
    <tr align="center">
        <td></td>
        <td>belongarea</td>
        <td>所属地区</td>
        <td>单选</td>
        <td>地区分类</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>legalperson</td>
        <td>法人</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>taxpayernum</td>
        <td>纳税人登记号</td>
        <td>文本</td>
        <td></td>
    </tr>  
</table>


###### 银行账户

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="500px" colspan="4">银行账户</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="4">bank_doc</td>
    </tr>
    <tr align="center">
        <td>父实体：</td>
        <td colspan="4">客商档案</td>
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
        <td>bank</td>
        <td>开户银行</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>banknum</td>
        <td>银行账号</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>isdefault</td>
        <td>是否默认</td>
        <td>单选</td>
        <td>逻辑判断</td>
    </tr> 
    <tr align="center">
        <td></td>
        <td>remark</td>
        <td>备注</td>
        <td>文本</td>
        <td></td>
    </tr>
</table>


###### 收发货地址

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="500px" colspan="4">收发货地址</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="4">shipping_address</td>
    </tr>
    <tr align="center">
        <td>父实体：</td>
        <td colspan="4">客商档案</td>
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
        <td>address</td>
        <td>发货地址名称</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>link</td>
        <td>联系人</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>phone</td>
        <td>电话</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>isdefault</td>
        <td>是否默认</td>
        <td>单选</td>
        <td>逻辑判断</td>
    </tr> 
    <tr align="center">
        <td></td>
        <td>place</td>
        <td>地点</td>
        <td>文本</td>
        <td></td>
    </tr>
</table>