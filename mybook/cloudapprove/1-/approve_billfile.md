## 修改表单数据最佳实践

### 应用场景

在用友的业务系统做了审批流，
需要在审批流的某个环节，修改表单中的数据

#### 第一步：下载测试Demo

代码Demo git地址[链接](https://github.com/YYETST/cloud-approve.git)

#### 第二步：配置application.properties

如何配置请查看文档[权限验证](/mybook/cloudapprove/2-/Identity_verify.md)

#### 第三步：加载云审批jar包到项目中

src/main/resources/lib

#### 第四步：注册审批监听事件

如何使用查看文档[审批事件监听注册](/mybook/cloudapprove/3-/createlisten.md)

#### 第五步：接收监听数据

如何使用请查看文档[接收监听数据](/mybook/cloudapprove/4-/receive_approve_data.md)

#### 第六步：获取表单数据(根据需求选择接口文档)

1. 如何使用请查看文档[获取表单数据](/mybook/cloudapprove/5-/billcontent.md)
2. 如何使用请查看文档[获取表单附件信息](/mybook/cloudapprove/7-/billfiles.md)

#### 第七步：修改表单数据

1. 如何使用请查看文档[更新表单数据](/mybook/cloudapprove/8-/updateBill.md)





