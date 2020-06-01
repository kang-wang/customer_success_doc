## 1 概述

### 1.1 前提

第三方需要在diowrk或yonsuite上自建应用，并且拥有完整的审批业务系统。

### 1.2 业务场景

第三方应用已有审批流程的业务系统，需要在友空间上进行集成，支持在友空间上进行查看审批，审批操作。

## 2 配置集成方式

### 2.1 进入审批中心

以管理员身份进入审批中心
<img src="/mybook/approve_center/1-/images/1.png"/><p align="center">图 1</p>

### 2.2 进入配置页

点击右上角中的设置键进入配置页
<img src="/mybook/approve_center/1-/images/2.png"/><p align="center">图 2</p>

### 2.3 新增应用

单击右侧的添加应用选择要添加的应用，点击提交在审批中心新增一个应用
<img src="/mybook/approve_center/1-/images/3.png"/><p align="center">图 3</p>

### 2.4 设置

鼠标放到新出现的应用图标上，点击设置
<img src="/mybook/approve_center/1-/images/4.png"/><p align="center">图 4</p>

### 2.5 配置地址

在数据来源中填上自己的服务地址即可，这个地址就是后续接入中审批中心会调用的地址
<img src="/mybook/approve_center/1-/images/5.png"/><p align="center">图 5</p>

## 3 接入基本原理

### 2.1 基本方式

审批中心向外部接入系统提供的地址发起请求，接入系统需要按照请求数据中提供的操作类型使用相应的业务数据完成逻辑处理，并按照指定的格式返回数据。

### 2.2 调用流程

下图说明了一次业务请求的基本流程
<img src="/mybook/approve_center/1-/images/6.png"/><p align="center">图 6</p>

审批中心会在每次调用第三方接口前检查是否有对应人员的认证信息缓存，如果没有，则会请求获取认证信息的接口,将认证相关信息放入请求数据中，再发送具体的业务请求。
请求基本格式说明
```
url:
xxx.xxx/xxx?lang=zhs&isDiwork=true

headers:
token: xxxxx

body:
{    
    "action": "",     
    "businessData": { 
    },
    "authData": {
    }
}
```

|参数名|类型|位置|备注
|:--|:--|:--|:--|:--
|lang|	String|	query	|多语判断字段 取值 zhs-简体 zht-繁体 en-英文
|isDiwork|	boolean|	query	|是否为diwork空间
|token|	String	|header	|验证token，来自获取认证信息接口，从authData中取出单独放置于header中，便于校验处理，如果获取认证信息的返回中不包含token，则不会传此header。
|action	|String|	body	|操作类型，外部接入系统通过此字段来区分不同的操作类型，并完成对应逻辑处理
|businessData|	JSON|	body|	业务数据载荷，包含一次请求所需的业务数据，如访问来源，分页大小，任务ID等，根据不同的操作类型，内容会有所不同。
|authData|	JSON	|body	|认证数据载荷，来自获取认证信息的接口，去除token字段及其过期时间字段后放入，外部接入系统用于用户、权限、加密等验证的字段，由外部接入系统提供和使用，审批中心不关心其内容。

### 2.3 接口文档
https://open.diwork.com/#/docs/md2docs/open-api-doc?id=xietong&section=79
<img src="/mybook/approve_center/1-/images/7.png"/><p align="center">图 7</p>

## 3 接入流程示例

### 3.1 审批列表页面

首先配置数据来源，数据来源地址可以填写
`http://approve002.test.app.yyuap.com/approveCenter` 
（该地址提供的接口遵循接口文档格式，是模拟了业务系统的审批流程,仅用于测试）
<img src="/mybook/approve_center/1-/images/8.png"/><p align="center">图 8</p>

可以在审批中心对应应用看到从业务系统获取到的审批数据，如图所示：
<img src="/mybook/approve_center/1-/images/10.png"/><p align="center">图 9</p>

- 调用流程：
点开审批中心->获取认证->获取待办数量->获取审批列表1

- 详细说明：
调用获取认证接口会自动拼接参数code，可通过code拿到当前登录用户信息，从而实现获取当前用户的审批列表和审批数量。
若需要直接查看接口的返回数据详情，可直接通过postman进行测试，只需要在body中传不同的action即可。例如：{ "action": "getAuthData"}
<img src="/mybook/approve_center/1-/images/9.png"/><p align="center">图 10</p>

- 注意：批量审批的按钮若需要放开权限的话，需要和审批中心对接负责人联系，并且提供租户id和数据源地址。

### 3.2 审批详情页面

点击列表页面的某一行数据会根据审批任务列表接口返回数据的url跳转到详情页面，如果第三方没有提供页面，可将url设置为 "url": "USER_CUSTOMAPPROVE"，会使用审批中心提供的默认页面。
<img src="/mybook/approve_center/1-/images/15.png"/><p align="center">图 11</p>

同时会调用元数据接口，根据元数据中的services数据再去调不同的详情接口。

- 调用流程：
点开列表详情->获取认证->元数据接口->根据元数据中service调其他接口
<img src="/mybook/approve_center/1-/images/11.png"/><p align="center">图 12</p>

- 详细说明：
若需要查看测试案例中元数据接口的数据可通过postman，action传pageMeta即可，例如：{ "action": "pageMeta"}。
<img src="/mybook/approve_center/1-/images/12.png"/><p align="center">图 13</p>

在返回的数据中，根据services中的数据再去访问不同的接口。也就是说，自定义详情中的接口是由元数据接口控制的，如下图，元数据接口返回的services中resp有哪些，就会自动调用相应的接口。
<img src="/mybook/approve_center/1-/images/13.png"/><p align="center">图 14</p>

审批列表详情页面如图所示：
<img src="/mybook/approve_center/1-/images/14.png"/><p align="center">图 15</p>







