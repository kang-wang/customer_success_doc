# 常见问题

## 使用说明及注意事项

## 常见问题
####1.点击推送ticket时报错，如下图所示
<div align=center>
<img src="/mybook/isv/2-/images/1.png"/>
</div>
<p align="center">图 1</p>

#### 解决办法
解密需要替换JDK 的security 文件，路径javahome/jre/lib/security/
JDK文件在项目中resources->lib

#### 2.获取token失败---suiteTicket不存在？如下图所示
<div align=center>
<img src="/mybook/isv/2-/images/2.png"/>
</div>
<p align="center">图 2</p>

#### 解决办法
ticket约20分钟过期，在没有启动自动推送ticket时，需手动获取suiteTicket，重新手动推送ticket即可

#### 3.注册服务商时漏掉或忘记勾选某一项，如yonsuite，或yonbip

#### 解决办法
如果一开始没有选择的话，可以联系服务商管理人员 kangwang@yonyou.com、niuhong@yonyou.com。

#### 4.融合对接，需要沙箱吗？

#### 解决办法
是有沙箱的，需要先通过沙箱来模拟购买的测试过程

#### 5. 通过用户接口获取用户信息 邮箱，手机号码，显示的都加密的数据，能否显示明文。

#### 解决办法
如下图
<div align=center>
<img src="/mybook/isv/2-/images/3.png"/>
</div>
<p align="center">图 3</p>

#### 6.在沙箱授权推送的报文 邮箱，手机号码，能否显示明文。

#### 解决办法
想要修改推送过来的订单信息中的参数信息或者显示方式联系对接人员修改模板

#### 7. 友互通账号中的手机号，邮箱是必填项吗？

#### 解决办法
友户通的账号是 手机号或者邮箱有一个是必填项，可以只有手机号，或者只有邮箱。

#### 8.沙箱环境授权后，在菜单里看不到配置的应用菜单。

#### 解决办法
只有开通沙箱环境的人才能看到菜单

#### 9. 沙箱环境，通过菜单点击 跳转到应用连接没有code参数  

#### 解决办法
在集成免登策略一定一定选择友空间才能获取到code免密登录友空间，如下图所示
<div align=center>
<img src="/mybook/isv/2-/images/4.png"/>
</div>
<p align="center">图 4</p>

#### 10. 租户的名称，从哪里获取？

#### 解决办法
管理员可在管理租户的地方看到
<div align=center>
<img src="/mybook/isv/2-/images/5.png"/>
</div>
<p align="center">图 5</p>