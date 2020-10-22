#### 第一步：下载测试Demo

代码Demo git地址[链接](https://github.com/YYETST/cloud-approve.git)

#### 第二步：配置application.properties

如何配置请查看文档[权限验证](/mybook/cloudapprove/2-/Identity_verify.md)

#### 第三步：加载云审批jar包到项目中

src/main/resources/lib

#### 获取sign

一个接口调用一次就可以了
url不变，租户id不变，sign是不会变的,
在接口中写死就可以了

SignTest.getMySendTotal()
在方法内部填写自己请求的url即可获取到sign


<div align=center>
<img src="/mybook/cloudapprove/12-/images/1.png"/>
</div>
<p align="center">图 1</p>