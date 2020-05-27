## 权限验证
所有的接口调用前都需要传入权限验证参数
- - -
#### 版本 ####
v1
- - - 
#### 参数 ####

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="100px"></td>
        <td width="100px">必选</td>
        <td width="150px">类型及范围</td>
        <td width="200px">说明</td>
    </tr>
    <tr align="center">
        <td>server</td>
        <td>true</td>
        <td>string</td>
        <td>云审url</td>
    </tr>
    <tr align="center">
        <td>tenant</td>
        <td>true</td>
        <td>String</td>
        <td>租户id</td>
    </tr>
    <tr align="center">
        <td>clientToken</td>
        <td>true</td>
        <td>String</td>
        <td>客户端秘钥-获取方式请看注意事项</td>
    </tr>
    <tr align="center">
        <td>source</td>
        <td>true</td>
        <td>String</td>
        <td>请看注意事项</td>
    </tr>    
</table>

- - - 

#### 注意事项 ####

- - - 

测试代码中有demo

BaseService.getBaseParam()


server参数值

```
https://ys.yonyoucloud.com/ubpm-web-rest/

```

tenant获取租户id方式

```
登录业务系统，随便一个页面
按F12打开浏览器控制台
```

<div align=center>
<img src="/mybook/cloudapprove/2-/images/1.png"/>
</div>
<p align="center">图 1</p>


获取clientToken
<div>
登录业务系统【数字化建模】-》【流程管理】-》【接入信息】
点击导出key
</div>

<div align=center>
<img src="/mybook/cloudapprove/2-/images/2.png"/>
</div>
<p align="center">图 2</p>


获取source

<div>
登录业务系统，打开自己创建的审批流的流程设计器
按F12打开浏览器控制台
</div>
<div style="color: red">
appsource就是咱们这里用到的source
不是图中的source！
不是图中的source！！
不是图中的source！！！！
</div>

<div align=center>
<img src="/mybook/cloudapprove/2-/images/3.png"/>
</div>
<p align="center">图 3</p>


#### 代码示例 ####

```
public BaseParam getBaseParam(){
        BaseParam baseParam = new BaseParam();
        baseParam.setServer(base_url);
        baseParam.setTenant(teant);
        baseParam.setClientToken(approveToken);
        baseParam.setSource(source);
        return baseParam;
}

```



