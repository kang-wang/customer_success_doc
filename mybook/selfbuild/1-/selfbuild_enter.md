# 入门
## 一. 概述
#### 1.1. 业务场景

企业自建应用是企业为了满足业务拓展需求，由企业内部开发人员或者委托第三方软件 服务商开发的，仅供企业用户内部人员使用的应用。企业需要将自建应用接入到用友云工作 台，或者需要对接用友开放平台对外开放的 OpenAPI，则需要企业创建应用，并对应用赋予 接口权限，开发人员才能够进行免登和接口调用开发。 线上文档地址：https://open.diwork.com/#/doc-center/ 如需要更详细信息请查看

<div align=center>
<img src="/mybook/selfbuild/1-/images/1.png"/>
</div>
<p align="center">图 1</p>

#### 1.2. 使用流程

<div align=center>
<img src="/mybook/selfbuild/1-/images/2.png"/>
</div>
<p align="center">图 2</p>

## 二. 开通测试租户

## 三. 开发流程
#### 3.1. 创建应用
企业管理员登录用友云工作台（diwork的访问地址https://www.diwork.com；yonsuite的访问地址https://yonsuite.diwork.com） 。注意必须是企业管理员用户，否则没有应用管理节点权限。选择租户，点击左上角的快捷应用中的 “数字化建模”-“系统管理”-“我的应用”，点击“我的应用”菜单，如下图所示：

<div align=center>
<img src="/mybook/selfbuild/1-/images/3.png"/>
</div>
<p align="center">图 3</p>

进入我的应用页面，点击【添加自建应用】-【集成开发】，如下图所示：

<div align=center>
<img src="/mybook/selfbuild/1-/images/4.png"/>
</div>
<p align="center">图 4</p>

打开添加自建应用页面，填写应用基本信息，如下图所示：

<div align=center>
<img src="/mybook/selfbuild/1-/images/5.png"/>
</div>
<p align="center">图 5</p>

返回到应用列表，点击服务列表，如下图所示：（如果只是接口通信，则跳过后续操作，不用做服务列表，直接查看2.2章节）

<div align=center>
<img src="/mybook/selfbuild/1-/images/6.png"/>
</div>
<p align="center">图 6</p>

点击【添加自建服务】，打开添加自建服务页面，填写服务信息，如下图所示：

<div align=center>
<img src="/mybook/selfbuild/1-/images/7.png"/>
</div>
<p align="center">图 7</p>

字段|说明
---|---
服务基本属性配置|
服务名称|名称不能多于6个汉字或者12个字母
服务图标|支持选择默认图标和上传本地图标2种方式；本地图标尺寸必须为120*120的JPG、GIF、PNG图片，且尺寸不大于5M
发布客户端|应用的客户端类型，包括 Web端、PC Client端、友空间、微信、钉钉，至少选择一类，选择后需要填写相应的配置信息
Web端，即用友工作台|
web端主页|当客户端选择web端时显示，填写web端的主页地址，必填项
web端打开方式|在当前页面打开和在新页面打开;当前页面表示就在浏览器的当前页面跳转到web端的主页地址;新页面表示在新窗口或新的标签页打开web端的主页地址
集成免登策略|选项包括：无、友空间;选择友空间则按照友空间的免登机制进行免登
PC Client端，即友空间桌面端|
PC客户端主页|输入在友空间桌面端打开时跳转地址
pcClient打开方式|支持PC客户端内、浏览器新页、本地3种方式
友空间，即友空间APP端|
app原生导航|如果移动应用使用友空间APP原生的导航栏则勾选是，如果使用应用自己的导航栏则勾选否
是否原生|移动应用是原生开发的应用，还是H5轻应用
移动端主页|当是否原生选择否时显示，填写移动端的主页地址
summerId|请输入上传到IUAP平台的安装包ID
推荐到移动端首页|当前移动应用是否推荐到友空间APP首页，如果推荐，是放在最前面，还是最后面

#### 3.2. 接口授权

登录用友云工作台，点击左上角菜单按钮，选择【数字化建模】-【系统管理】-【我的应用】菜单，打开【我的应用】页面，点击【开放平台】按钮

<div align=center>
<img src="/mybook/selfbuild/1-/images/8.png"/>
</div>
<p align="center">图 8</p>

```
如果需要申请接口请查看线上文档【企业自建应用接入】->【开发流程】->【申请开通】
```
[接口授权操作指南](https://open.diwork.com/#/doc-center/docDes/doc?code=open_jrwd&section=c3e36e4b9e074578890bc4b87fa425e0)

打开【开放平台】页面，点击【API授权】按钮，点击【新增】按钮，弹出窗口打开【新增API授权】页面，选择要授权的API分类

<div align=center>
<img src="/mybook/selfbuild/1-/images/9.png"/>
</div>
<p align="center">图 9</p>

## 四. 代码Demo

#### 4.1. git地址

[测试Demo](https://github.com/YYETST/ZJTSET.git)

```
- 该demo为springboot项目，在resources/application.properties里面配置<font color=#FF0000 > `app.key` `app.secret` `app.code`</font> 三个参数，启动CorpDemoApplication 即可测试。
```

#### 4.2. 注意事项

```
 查看 `app.key` `app.secret` `app.code
【我的应用】->选择自己建的应用->浮动行上点击右侧【开放平台】->【API授权】
```
<div align=center>
<img src="/mybook/selfbuild/1-/images/10.png"/>
</div>
<p align="center">图 10</p>

#### 4.2. 接口文档
[获取access token接口文档](https://open.diwork.com/#/doc-center/docDes/doc?code=open_jrwd&section=022c941650ae4989af7dd6ac7fd4d412)

[免登接口文档](https://open.diwork.com/#/doc-center/docDes/api?code=diwork&section=88f2d60a-8b83-4e31-9505-e91a3fd3a3d5)
