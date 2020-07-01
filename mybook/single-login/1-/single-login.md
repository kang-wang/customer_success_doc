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

#### 1.3. 企业认证并绑定企业账号

如当前企业账号未完成企业认证，可访问企业服务中心，按要求完成企业认证并绑定企业账号。企业服务中心地址：https://apcenter.yonyoucloud.com/apptenant

<div align=center>
<img src="/mybook/single-login/1-/images/8.png"/>
</div>
<p align="center">图 8</p>

<div align=center>
<img src="/mybook/single-login/1-/images/9.png"/>
</div>
<p align="center">图 9</p>
<div align=center>
<img src="/mybook/single-login/1-/images/10.png"/>
</div>
<p align="center">图 10</p>

#### 1.4. 获得集成认证中心编码

新建集成认证中心后，系统会为当前三方认证中心分配一个编码
<div align=center>
<img src="/mybook/single-login/1-/images/11.png"/>
</div>
<p align="center">图 11</p>

#### 1.5. 获得集单点登录code

对接开放平台接口，获取单点登录code，详细接口文档如下：<br>
https://open.diwork.com/#/doc-center/docDes/api?code=diwork&section=d1c38bd20e2e41fbaf200c4fdf883d9b

调用接口需要先完成开放平台access_token鉴权。详情见1.8

#### 1.6. 使用code拼接单点登录url

使用单点code拼接登录地址，规则如下https://euc.diwork.com/cas/thirdOauth2CodeLogin?thirdUCId={thirdUcId}&code={code}&service={service}<br>
  参数描述：<br>
thirdUcId	三方认证中心编码<br>
Code	调用开放平台接口返回的code<br>
Service	登录成功后的跳转地址<br>

service参数需要进行一次encode，后端可以采用URLEncode，前端可以使用encodeURIComponent<br>
例如：encodeURIComponent('https://www.diwork.com/login')

常用service举例：<br>
diwork	https://www.diwork.com/login <br>
Yonsuite	https://yonsuite.diwork.com/login

#### 1.7. 账号绑定与解绑

用户访问单点登录地址，首次登陆需要输入用友云账号和验证码，完成账号绑定。<br>
已完成绑定的账号可以凭code直接登录用友云。<br>
用户可在用友云账号中心https://euc.diwork.com进行解绑，也可以由管理员在集成认证中心-用户管理里解绑。

#### 1.8.  开放平台对接示意
新建应用 -> 开放平台AK获取 -> 接口授权 -> 开发；详细接入过程可参考开放平台-企业自建应用接入文档：<br>
https://open.diwork.com/#/doc-center/docDes/doc?code=open_jrwd&section=022c941650ae4989af7dd6ac7fd4d412
<div align=center>
<img src="/mybook/single-login/1-/images/12.png"/>
</div>
<p align="center">图 12</p>

<div align=center>
<img src="/mybook/single-login/1-/images/13.png"/>
</div>
<p align="center">图 13</p>
<div align=center>
<img src="/mybook/single-login/1-/images/14.png"/>
</div>
<p align="center">图 14</p>
<div align=center>
<img src="/mybook/single-login/1-/images/15.png"/>
</div>
<p align="center">图 15</p>

<div align=center>
<img src="/mybook/single-login/1-/images/16.png"/>
</div>
<p align="center">图 16</p>
<div align=center>
<img src="/mybook/single-login/1-/images/17.png"/>
</div>
<p align="center">图 17</p>

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


