# 环境安装

## 准备工具

#### github

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="200px">创建一个空仓库</td>
    </tr>
</table>

#### 前端

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="200px">工具</td>
        <td width="300px">教程</td>
    </tr>
    <tr align="center">
        <td width="200px">node.js</td>
        <td width="300px">https://www.cnblogs.com/zhouyu2017/p/6485265.html</td>
    </tr>
    <tr align="center">
        <td>vscode</td>
        <td>https://blog.csdn.net/weixin_41350225/article/details/84500614
        </td>
    </tr>
</table>

#### 后端

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="200px">工具</td>
        <td width="300px">教程</td>
    </tr>
    <tr align="center">
        <td width="200px">jdk 1.8</td>
        <td width="300px">https://blog.csdn.net/weixin_44084189/article/details/98966787
        </td>
    </tr>
    <tr align="center">
        <td>IDEA 2018及以上</td>
        <td>https://blog.csdn.net/weixin_30511039/article/details/99637435
        </td>
    </tr>
    <tr align="center">
        <td>maven 3.2及以上</td>
        <td>https://www.cnblogs.com/xihehua/p/9639045.html
        </td>
    </tr>
    <tr align="center">
        <td>mysql 5.7.11及以上</td>
        <td>https://www.cnblogs.com/water-1/p/10802256.html
        </td>
    </tr>
</table>

## 创建引擎

填写信息后，我们会进行审核，并分配资源.请耐心等待
审核通过后，系统会自动部署流水线

<div align=center>
<img src="/mybook/developergame/professional/1-/images/1.png"/>
</div>
<p align="center">图 1</p>

## 下载代码

进入自己的github里面拉取代码，方便版本管理

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="200px">be后缀</td>
        <td width="300px">后端</td>
    </tr>
    <tr align="center">
        <td width="200px">fe后缀</td>
        <td width="300px">前端</td>
    </tr>
</table>

## 项目运行

#### 前端修改

将env.json覆盖到本地

<div align=center>
<img src="/mybook/developergame/professional/1-/images/16.png"/>
</div>
<p align="center">图 16</p>

<div align=center>
<img src="/mybook/developergame/professional/1-/images/17.png"/>
</div>
<p align="center">图 17</p>

覆盖env.json后，再进行编辑

<div align=center>
<img src="/mybook/developergame/professional/1-/images/2.png"/>
</div>
<p align="center">图 2</p>

<div align=center>
<img src="/mybook/developergame/professional/1-/images/3.png"/>
</div>
<p align="center">图 3</p>


#### 后端项目修改

- 登录YonBuilder专业版 https://developer.yonyoucloud.com/#/

<div align=center>
<img src="/mybook/developergame/professional/1-/images/4.png"/>
</div>
<p align="center">图 4</p>

<div align=center>
<img src="/mybook/developergame/professional/1-/images/5.png"/>
</div>
<p align="center">图 5</p>

<div align=center>
<img src="/mybook/developergame/professional/1-/images/12.png"/>
</div>
<p align="center">图 12</p>

- 替换uimeta-sdk.properties

```
# redis\u7F13\u5B58index
mdd.uimeta.prop.uimetaRedisIndex=6
# viewmodel\u662F\u5426\u5E94\u7528redis \u5916\u90E8\u7F13\u5B58
mdd.uimeta.prop.isRedisCache=true
# viewmodel\u662F\u5426\u5E94\u7528 \u4E0A\u4E0B\u6587\u7F13\u5B58
mdd.uimeta.prop.isContextCache=false
# uimeta \u89C4\u5219\u7EA7\u522B\u5B9A\u4E49 ruleLvs; \u591A\u4E2A\u7EA7\u522B\u9017\u53F7\u5206\u9694
mdd.uimeta.prop.uimetaRuleLvs=common,uimeta
# \u662F\u5426\u8D70metaService\u670D\u52A1
mdd.uimeta.prop.isMetaServer=true
# \u7EDF\u4E00\u5B58\u50A8\u670D\u52A1rest\u5730\u5740
mdd.uimeta.prop.metaServerUrl=http://2020.yonyoucloud.com/mdf

```


- 如果使用的是idea ,请查看一下启动项配置是否正确

<div align=center>
<img src="/mybook/developergame/professional/1-/images/6.png"/>
</div>
<p align="center">图 6</p>

<div align=center>
<img src="/mybook/developergame/professional/1-/images/7.png"/>
</div>
<p align="center">图 7</p>


#### 修改hosts

- 地址栏输入:  C:\Windows\System32\drivers\etc
- 将hosts复制到桌面修改再覆盖即可： 添加： 127.0.0.1  local.yonyoucloud.com

<div align=center>
<img src="/mybook/developergame/professional/1-/images/10.png"/>
</div>
<p align="center">图 10</p>

<div align=center>
<img src="/mybook/developergame/professional/1-/images/11.png"/>
</div>
<p align="center">图 11</p>

#### 启动项目

- 后端启动类 MDFApplication

<div align=center>
<img src="/mybook/developergame/professional/1-/images/8.png"/>
</div>
<p align="center">图 8</p>

- 前端编辑器中终端输入命令：  node bin.js

<div align=center>
<img src="/mybook/developergame/professional/1-/images/9.png"/>
</div>
<p align="center">图 9</p>


#### 访问

在应用中打开预览，然后更改为本地地址即可

<div align=center>
<img src="/mybook/developergame/professional/1-/images/13.png"/>
</div>
<p align="center">图 13</p>

<div align=center>
<img src="/mybook/developergame/professional/1-/images/14.png"/>
</div>
<p align="center">图 14</p>

<div align=center>
<img src="/mybook/developergame/professional/1-/images/15.png"/>
</div>
<p align="center">图 15</p>













