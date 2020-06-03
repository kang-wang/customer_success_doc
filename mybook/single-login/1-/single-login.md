# 单点登录Yonsuite
## 一. 集成认证中心
#### 1.1. 购买集成认证中心(免费)

使用管理员账号登录
https://www.diwork.com或者https://yonsuite.diwork.com（自己使用的业务系统）
访问数字化建模-系统管理-我的应用-应用市场，购买集成认证中心。开通成功后，系统管理下会多出集成认证中心菜单;

<div align=center>
<img src="/mybook/single-login/1-/images/1.png"/>
</div>
<p align="center">图 1</p>

<div align=center>
<img src="/mybook/single-login/1-/images/2.png"/>
</div>
<p align="center">图 2</p>

<div align=center>
<img src="/mybook/single-login/1-/images/3.png"/>
</div>
<p align="center">图 3</p>

<div align=center>
<img src="/mybook/single-login/1-/images/4.png"/>
</div>
<p align="center">图 4</p>

#### 1.2. 新增集成认证

访问数字化建模-系统管理-集成认证中心，点击新增集成认证

<div align=center>
<img src="/mybook/single-login/1-/images/5.png"/>
</div>
<p align="center">图 5</p>

<div align=center>
<img src="/mybook/single-login/1-/images/6.png"/>
</div>
<p align="center">图 6</p>

## 二. 单点登录流程图

#### 2.1. 前提条件

1. 通过 [服务商接入](mybook/isv/README.md) 或者 [自建接入](mybook/selfbuild/README.md)
已经获取到鉴权参数access_token。
原因：
【集成认证中心获取登录临时code】接口需要用到鉴权参数access_token

#### 2.2. 流程图

<div align=center>
<span style="color: red; text-align: left">
</span>
<img src="/mybook/single-login/1-/images/7.png"/>
</div>
<p align="center">图 7</p>


