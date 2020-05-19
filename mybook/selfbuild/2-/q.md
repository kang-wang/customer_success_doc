# 常见问题

## 使用说明及注意事项

- 该demo为springboot项目，在resources/application.properties里面配置<font color=#FF0000 > `app.key` `app.secret` `app.code`</font> 三个参数，启动CorpDemoApplication 即可测试。

- 查看验签流程：可以debug模式启动test下../yonbip/uspace/StaffTest.java的getStaffPageList()方法即可。

- 在调试接口的过程中如果遇到问题，请先看一下常见问题，是否能给您解答。

- 参考文档url： https://open.diwork.com/#/doc-center

## YonSuite 接口示例

## YonBIP 接口示例

#### 协同云--调用接口顺序：

###### 只调用接口的情况(适用于消息、待办等在自己应用服务器调接口的情况)
- 查看租户id-->获取token接口-->获取用户列表-->其它业务接口

###### 使用用友控制台、移动友空间、桌面友空间等需要点击操作的情况
- 获取token-->应用免登-->其它业务

###### 常用获取员工信息接口流程
- 获取token接口-->免密登录接口-->根据手机号或者邮箱查询员工-->根据id查询职位信息
示例参考StaffTest.java 和 JobTest.java 以及 OrgStaffTest.java

## 常见问题

#### 如何获取code

- 在用友的系统中打开自建应用时，会给填写的url上拼写参数code，从request中获取即可
- 查看测试UserInfoListTest

#### 不登陆如何获取租户id

- 一个租户的租户id是不会变的，直接写死即可

#### 有些接口的appId或者ykjId如何获取

- 查看测试类UspaceListTest

#### 请求数据中包含需要打开的地址怎么获取code
- 应用场景：代办、扫描
url+?code=${esncode}
例如: http://www.baidu.com?code=${esncode} 

#### 为什么我建的应用没有开放平台按钮?
- 排查下您建的应用是否是快速链接?
快速链接：只支持服务列表
自建应用：支持开放平台、服务列表

#### 服务列表按钮的应用场景是什么?
- 支持将第三方的链接集成到用友的数字化控制台、PC版友空间、移动版友空间

#### 开放平台按钮的应用场景是什么?
- 支持API授权，订阅消息。
适用于需要做免密，调用业务接口进行交互的场景。
为保证某些核心数据的一致性，提供订阅消息的服务.如：
新增了一个员工，用友会推送数据给第三方，告诉他们数据变更了
提示他们重新获取数据。来保证数据的一致性

