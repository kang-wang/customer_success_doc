## 第三方发起流程最佳实践

### 应用场景

在用友系统配置了审批流，使用第三方系统提交单据数据并发起流程

#### 第一步：下载测试Demo

代码Demo git地址[链接](https://github.com/YYETST/cloud-approve.git)

#### 第二步：配置application.properties

如何配置请查看文档[权限验证](/mybook/cloudapprove/2-/Identity_verify.md)

#### 第三步：加载云审批jar包到项目中

src/main/resources/lib

#### 第四步：通过自建接入获取用户的yhtuserid

只需要配置应用信息，获取到accessToken。然后调用根据手机号获取用户信息接口即可

示例：请下载自建接入的demo

```
UserInfoListTest.getUserInfoByMobile()
```

[自建接入](/mybook/selfbuild/README.md)

#### 第五步：保存表单并发起流程

[保存表单并发起流程](/mybook/cloudapprove/15-/README.md) 

 

