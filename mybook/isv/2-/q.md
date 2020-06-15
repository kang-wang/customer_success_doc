# 常见问题

## 使用说明及注意事项

##常见问题
####1.点击推送ticket时报错，如下图所示
<div align=center>
<img src="/mybook/isv/2-/images/1.png"/>
</div>
<p align="center">图 1</p>

####解决办法
解密需要替换JDK 的security 文件，路径javahome/jre/lib/security/
JDK文件在项目中resources->lib

#### 2.获取token失败---suiteTicket不存在？如下图所示
<div align=center>
<img src="/mybook/isv/2-/images/2.png"/>
</div>
<p align="center">图 2</p>

####解决办法
ticket约20分钟过期，在没有启动自动推送ticket时，需手动获取suiteTicket，重新手动推送ticket即可