# 入门
## 一. 概述
#### 1.1. 业务场景

服务商（ISV）是指独立于企业、用友之外的第三方软件提供商。应用服务商在开放平台先进行服务商入驻，再创建开发生态应用，并上架到用友云应用市场。企业管理员在用友云应用市场中购买应用服务商发布的应用后，开放平台会通知应用服务商企业的购买行为，同时为应用服务商颁发获取企业数据的授权信息，应用服务商根据授权信息为企业开通应用，并获取需要的企业相关的业务信息。企业的应用成功开通后，企业员工即可通过YonSuite平台来使用应用服务商发布的应用。
用友开放平台为服务商提供了开放平台门户、开放平台控制台2个平台。
开放平台门户作为用友云开放生态能力宣传的门户，主要面向企业和服务商，提供用友各产品介绍，方便企业和服务商了解用友云产品；提供服务商接入流程说明，引导生态伙伴（即服务商）入驻；提供文档中心，包括应用开发文档、API文档、消息文档，详细描述了应用开发流程、对外开放的OpenAPI、消息事件和应用开发流程，引导开发者进行应用的开发、API接入开发和事件订阅；提供服务商入驻、开放平台控制台登录、应用市场、社区交流和支持中心的统一入口。
服务商注册后就可通过开放平台门户登录进入开放平台控制台，开放平台控制台是面向服务商管理员和开发者的，提供权限管理、API接入申请、应用管理、API授权、事件订阅、沙箱环境等功能。
线上文档地址：https://open.diwork.com/#/doc-center/
如需要更详细信息请查看

#### 1.2. 使用流程

<div align=center>
<img src="/mybook/isv/1-/images/1.png"/>
</div>
<p align="center">图 1</p>

## 二. 开放平台

#### 2.1. 注册开放平台

进入开放平台首页（https://open.diwork.com）， 点击顶部导航栏的【注册】按钮或者门户首页里的【立即入驻】按钮。用友云使用统一的用户体系，使用过用友云的用户无需注册，可以直接登陆。

<div align=center>
<img src="/mybook/isv/1-/images/2.png"/>
</div>
<p align="center">图 2</p>

填写注册信息

<div align=center>
<img src="/mybook/isv/1-/images/3.png"/>
</div>
<p align="center">图 3</p>

#### 2.2. 应用服务商认证

登陆后点击控制台

<div align=center>
<img src="/mybook/isv/1-/images/4.png"/>
</div>
<p align="center">图 4</p>

首次进入开放平台控制台，系统提示创建服务商，如下图所示：

<div align=center>
<img src="/mybook/isv/1-/images/5.png"/>
</div>
<p align="center">图 5</p>

点击【开始创建】按钮，打开平台服务商认证页面，填写服务商基本信息，上传企业资质认证文件，提交审核。

<div align=center>
<img src="/mybook/isv/1-/images/6.png"/>
</div>
<p align="center">图 6</p>

用友云开放平台运营人员会在1-3个工作日内进行审核，审核通过后，服务商管理员即可登录服务商门户使用相应功能，服务商状态变更为“已认证”，如下图所示：

<div align=center>
<img src="/mybook/isv/1-/images/7.png"/>
</div>
<p align="center">图 7</p>

#### 2.3. 创建生态应用

点击【新增应用】按钮，打开生态应用创建向导页面

<div align=center>
<img src="/mybook/isv/1-/images/8.png"/>
</div>
<p align="center">图 8</p>

根据提示信息填写应用信息

<div align=center>
<img src="/mybook/isv/1-/images/9.png"/>
</div>
<p align="center">图 9</p>

注意：授权回调URL。是用来接收回调Ticket、通知消息的地址。需要能够外网访问。详细信息请参考第三章节授权流程，示例代码：PushAuthController
● 点击【下一步】，进入第二步维护应用功能页面，直接点击确定即可,（仅是接口通信，不需要配置应用功能）然后返回生态应用首页。

<div align=center>
<img src="/mybook/isv/1-/images/10.png"/>
</div>
<p align="center">图 10</p>

<div align=center>
<img src="/mybook/isv/1-/images/11.png"/>
</div>
<p align="center">图 11</p>

#### 2.4. API授权

点击API授权

<div align=center>
<img src="/mybook/isv/1-/images/12.png"/>
</div>
<p align="center">图 12</p>

新增

<div align=center>
<img src="/mybook/isv/1-/images/13.png"/>
</div>
<p align="center">图 13</p>

选择需要的API点击确定

<div align=center>
<img src="/mybook/isv/1-/images/14.png"/>
</div>
<p align="center">图 14</p>

## 三. 企业授权管理

#### 3.1.代码示例

###### 3.1.1. 线上git地址

```
https://github.com/YYETST/YSAPI

内涵验证示例代码和常用接口调用示例代码，会持续更新
```
###### 3.1.2. 注意事项

请配置application.properties

<div align=center>
<img src="/mybook/isv/1-/images/15.png"/>
</div>
<p align="center">图 15</p>

解密需要替换JDK的security文件，路径javahome/jre/lib/security/
(这里提供的是SUNJDK1.8 ，IBM的请自己下载)

<div align=center>
<img src="/mybook/isv/1-/images/16.png"/>
</div>
<p align="center">图 16</p>

获取业务接口前请设置租户ID

<div align=center>
<img src="/mybook/isv/1-/images/17.png"/>
</div>
<p align="center">图 17</p>

测试状态如何获取租户id--仅仅只是测试使用，注意！注意！！注意！！！
正常情况应通过订单来获取租户id

<div align=center>
<img src="/mybook/isv/1-/images/18.png"/>
</div>
<p align="center">图 18</p>


PushAuthController手动或者自动获取suiteTicket

<div align=center>
<img src="/mybook/isv/1-/images/19.png"/>
</div>
<p align="center">图 19</p>


#### 3.2.授权流程

<div align=center>
<img src="/mybook/isv/1-/images/20.png"/>
</div>
<p align="center">图 20</p>

###### 3.3.1. 授权流程概述

服务商的生态应用访问开放平台的OpenAPI，需要从开放平台获取访问令（access_token），访问令牌必须传递应用的appkey、appSecret、ticket和授权企业的租户I（tenantid）4个参数才能获取到。
应用的appKey和appSecret2个参数在服务商创建生态应用时开放平台会自动生成，可以从应用详情页面获取到，如下图所示：

<div align=center>
<img src="/mybook/isv/1-/images/21.png"/>
</div>
<p align="center">图 21</p>

服务商给应用开启自动推送ticket后，开放平台会向应用基本信息里填写的回调URL不定期（约二十分钟）推送ticket信息，开发者需要持久化ticket，新的ticket推送会使之前的ticket失效。Ticket的自动推送需要开发者为应用开启自动推送后才开始，如下图红框部分所示：

<div align=center>
<img src="/mybook/isv/1-/images/22.png"/>
</div>
<p align="center">图 22</p>

在开发态时，开发者可以手工推送ticket。手工推送一次，平台就向应用的回调URL推送一次ticket，如下图所示：

<div align=center>
<img src="/mybook/isv/1-/images/23.png"/>
</div>
<p align="center">图 23</p>

企业租户购买应用后，开放平台会调用应用的回调url，推送购买租户的tenantId。服务商通过调用getAccessToken接口获取授权租户数据接口的访问令牌 access_token，该令牌有效期 2 小时，过期后需重新获取。在获得了access_token后，服务商就可以访问对应租户下的数据。

上述流程中推送应用ticket和推送授权租户tenantId信息，是通过调用回调接口来实现的。回调接口即在创建应用时填写的【回调 URL】，请确保该接口能在公网环境下访问。开放平台会向回调URL定时推送ticket，以及租户授权信息。服务商在收到推送的消息后需要返回“success”字符串，否则平台会一直尝试推送。开放平台的推送都是 post json形式，使用了BASE64 + AES + SHA1 加解密，具体加解密验签方式详见 demo 中的实现。服务商在调用 getAccessToken接口时也需要加签，加签算法为HmacSHA256，

```
具体实现请参考示例代码 
PushAuthController

```

###### 3.3.2. 接口文档

```
具体实现请参考示例代码 
PushAuthController

```

[接收应用ticket](https://open.diwork.com/#/doc-center/docDes/doc?code=open_jrwd&section=471c49a3799a483d82790ba9aaacfb52)

[接收授权租户ID和订单信息](https://open.diwork.com/#/doc-center/docDes/doc?code=open_jrwd&section=05c95ee214ba4514af7deef6c41d0c0e)

```
具体实现请参考示例代码 
IsvTokenTest
```
[获得调用接口令牌access_token](https://open.diwork.com/#/doc-center/docDes/doc?code=open_jrwd&section=90b8ad7a8bfd4f3e9e13011b6a0b6618)

```
具体实现请参考示例代码
业务接口调用 
eg：UserInfoTest  用户接口
```
<div align=center>
<img src="/mybook/isv/1-/images/24.png"/>
</div>
<p align="center">图 24</p>


## 四. 沙箱环境

为了方便服务商测试应用功能和应用购买流程，用友云开放平台提供了沙箱环境进行测试的机制，服务商可以开通沙箱环境，模拟企业的授权、使用流程。
目前用友开放平台以测试租户的方式提供沙箱环境；服务商在控制台可以给服务商可发布环境（yonsuite，diwork）开通相应环境的沙箱环境（即测试租户），且每个环境只能开通一个测试租户。
沙箱环境使用流程如下：

<div align=center>
<img src="/mybook/isv/1-/images/25.png"/>
</div>
<p align="center">图 25</p>

#### 4.1.开通沙箱环境操作

1)服务商管理员访问开放平台门户，登录开放平台控制台点击左侧菜单区的【应用管理】-【沙箱环境】菜单，打开沙箱环境页面，系统会根据当前服务商可以发布的环境进行显示，并展示发布环境的沙箱环境的开通情况。
沙箱环境未开通，如下图所示：

<div align=center>
<img src="/mybook/isv/1-/images/26.png"/>
</div>
<p align="center">图 26</p>

2)沙箱环境已开通，如下图所示：

<div align=center>
<img src="/mybook/isv/1-/images/27.png"/>
</div>
<p align="center">图 27</p>

3)选择要开通的发布环境，点击【开通】按钮，系统向指定发布环境发出开通沙箱环境请求，开通状态为【开通中】。
注：由于沙箱环境开通过程后台处理需要一段时间，且是异步过程，系统会每隔3秒刷新获取开通结果，请用户耐心等待开通结果，沙箱环境的开通状态必须为【已开通已初始化】时才可以开始使用沙箱环境
```
● 若发布环境为diwork，沙箱环境开通成功后，无需做初始化操作，开通状态直接为【已开通已初始化】
● 若发布环境为yonsuite，沙箱环境开通成功，还需要用户做初始化操作，开通状态为【已开通未初始化】，
    用户必须做完初始化后，沙箱环境的开通状态才会改为【已开通已初始化】
```

4)若yonsuite沙箱环境开通状态为【已开通未初始化】时，需要做初始化操作
● 点击【初始化】按钮 

<div align=center>
<img src="/mybook/isv/1-/images/28.png"/>
</div>
<p align="center">图 28</p>

系统打开yonsuite沙箱环境初始化页面，根据初始化向导进行初始化操作

<div align=center>
<img src="/mybook/isv/1-/images/29.png"/>
</div>
<p align="center">图 29</p>
<div align=center>
<img src="/mybook/isv/1-/images/30.png"/>
</div>
<p align="center">图 30</p>
<div align=center>
<img src="/mybook/isv/1-/images/31.png"/>
</div>
<p align="center">图 31</p>

返回控制台的沙箱环境列表页面，yonsuite沙箱环境的开通状态改为【已开通初始化中】

<div align=center>
<img src="/mybook/isv/1-/images/32.png"/>
</div>
<p align="center">图 32</p>

注：由于沙箱环境初始化过程后台处理需要一段时间，且是异步过程，系统会每隔3秒刷新获取初始化结果，请用户耐心等待，当开通状态为【已开通已初始化】时表示初始化完成。
开通沙箱环境的用户就是测试租户的租户管理员，租户管理员需要自行进入测试租户里增加其他管理员和开发者，其他人才可以使用

#### 4.2.应用授权

服务商管理员开通沙箱环境后，服务商开发者才可以给沙箱环境进行应用授权操作。
注：开发者若发现沙箱环境未开通，请联系服务商管理员先开通沙箱环境。
1.服务商管理员访问开放平台门户，登录开放平台控制台
2.点击左侧菜单区的【应用管理】-【生态应用】菜单，打开生态应用首页，选择要测试的应用，点击应用记录的【沙箱环境】按钮，如下图所示：

<div align=center>
<img src="/mybook/isv/1-/images/33.png"/>
</div>
<p align="center">图 33</p>
<div align=center>
<img src="/mybook/isv/1-/images/34.png"/>
</div>
<p align="center">图 34</p>
<div align=center>
<img src="/mybook/isv/1-/images/35.png"/>
</div>
<p align="center">图 35</p>
注：此处选择的领域和移动分类，授权成功后，平台会将当前应用及功能菜单发布到对应发布环境里的相应领域和移动分类下
3.返回到应用沙箱环境列表页面，若应用不是自动开通的，需要点击【确认授权】，该应用才真正发布到工作台的测试租户里；若应用是自动开通，则无需确认授权，直接就发布到工作台的测试租户里。授权成功后，操作按钮显示【重新授权】和【进入沙箱环境】按钮
<div align=center>
<img src="/mybook/isv/1-/images/36.png"/>
</div>
<p align="center">图 36</p>

4.若应用功能（菜单）有变化，可以通过点击【重新授权】按钮，重新将当前应用授权到相应工作台中，会重新将应用功能（菜单）发布到测试租户

---

## 五. 上架应用市场

<div align=center>
<img src="/mybook/isv/1-/images/37.png"/>
</div>
<p align="center">图 37</p>

1.若服务商是第一次申请上架应用，平台会让服务商先进行店铺认证，服务商管理员录入店铺认证信息，并提交申请
2.平台运营人员在云市场运营端进行店铺认证审核
3.服务商管理员或开发者在服务商控制台申请应用上架
4.平台运营人员在开放平台运营端进行应用上架审核，审核通过则应用发布到云市场进行销售

#### 5.1.店铺认证

平台会在服务商第一次申请上架应用的时候，跳转到店铺认证页面，让服务商录入店铺信息，提交申请等待运营人员进行审核；只有店铺认证审核通过后，服务商才能够申请上架应用；若服务商的店铺认证申请未审核通过，下次申请上架仍然会跳转到店铺信息页面。
1、在开放平台控制台点击左侧菜单区的【应用管理】-【生态应用】菜单，打开生态应用页面

<div align=center>
<img src="/mybook/isv/1-/images/38.png"/>
</div>
<p align="center">图 38</p>

2、点击【申请上架】按钮，服务商若是第一次申请上架应用，平台会跳转到店铺认证页面

<div align=center>
<img src="/mybook/isv/1-/images/39.png"/>
</div>
<p align="center">图 39</p>

3、录入店铺信息，点击页面下方的【保存】按钮，保存店铺信息信息，然后点击【提交审核】按钮，提交店铺认证申请，等待平台运营人员进行审核

<div align=center>
<img src="/mybook/isv/1-/images/40.png"/>
</div>
<p align="center">图 40</p>

#### 5.2.申请上架

1、在开放平台控制台点击左侧菜单区的【应用管理】-【生态应用】菜单，点击申请上架

<div align=center>
<img src="/mybook/isv/1-/images/41.png"/>
</div>
<p align="center">图 41</p>

2、点击【申请上架】按钮，若服务商的店铺认证申请已经审核通过，平台会跳转到应用申请上架页面

<div align=center>
<img src="/mybook/isv/1-/images/42.png"/>
</div>
<p align="center">图 42</p>

3、如实填写应用的上架信息。在“版本规格”页面，服务商可以指定产品价格、产品套餐等。所有信息填写完毕后，提交应用市场审核

<div align=center>
<img src="/mybook/isv/1-/images/43.png"/>
</div>
<p align="center">图 43</p>

4、应用上架审核通过后，应用即完成上架，应用的状态修改为【已上架】，用友云的企业租户可以在市场中购买使用服务商上架的应用

<div align=center>
<img src="/mybook/isv/1-/images/44.png"/>
</div>
<p align="center">图 44</p>


#### 5.3.购买应用

<div align=center>
<img src="/mybook/isv/1-/images/45.png"/>
</div>
<p align="center">图 45</p>


#### 5.4. 接收订单信息

<div align=center>
<img src="/mybook/isv/1-/images/46.png"/>
</div>
<p align="center">图 46</p>


