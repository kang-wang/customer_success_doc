## 前端工程安装与启动

### 安装前端相关环境

下载并安装Node.js：版本10.0及以上，执行默认安装配置即可；（自带NPM包管理工具）
Chrome浏览器，用于开发调试

| **名称** | **下载地址** | **访问密码** |
| :--- | :--- | :--- |
| 前后端软件包 | [前后端软件包](http://pan.yonyou.com/s/LJUJJYvQq0)  | xavt |



| **工具** | **教程** |
| --- | --- |
| node.js | [https://www.cnblogs.com/zhouyu2017/p/6485265.html](https://www.cnblogs.com/zhouyu2017/p/6485265.html) |
| vscode | [https://blog.csdn.net/weixin_41350225/article/details/84500614](https://blog.csdn.net/weixin_41350225/article/details/84500614) |


### 打开前端脚手架FE

使用VScode打开前端脚手架 后缀为FE

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/framework/images/5.png"/>
</div>
<p align="center">图 1</p>


### 修改配置文件 env.js

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/framework/images/2.png"/>
</div>
<p align="center">图 2</p>


```
"default": {
		"base_url": "http://local.yonyoucloud.com:8080",
		"tpl_url": "https://ms-dbox.yyuap.com/mdf",
		"report_url": "https://intelliv-dbox.yyuap.com",
		"print_url": "http://local.yonyoucloud.com:8080",
		"workflow_url": "https://yb-dbox.yyuap.com",
		"customize_button_url": "http://local.yonyoucloud.com:8080",
		"file_url": "https://ezone-dbox.yyuap.com/cooperation",
		"cooperation_url" : "https://ykj-esn-test.oss-cn-beijing.aliyuncs.com/suite/cooperation/build"
	}
```

#### 修改本地localhost

配置hosts文件
• 地址栏输入: C:\Windows\System32\drivers\etc

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/framework/images/3.png"/>
</div>
<p align="center">图 3</p>

将hosts复制到桌面修改再覆盖即可 -> 添加：127.0.0.1 local.yonyoucloud.com

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/framework/images/4.png"/>
</div>
<p align="center">图 4</p>

### 依次执行命令

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/framework/images/1.png"/>
</div>
<p align="center">图 5</p>

```

npm install ynpm-tool -g
ynpm install

```

### 启动前端

启动命令配置文件：package.json中

```
npm run debug:client
# windows用户：打开dos窗口--->项目根目录--->npm run debug:client
npm run debug:server
# windows用户：打开dos窗口--->项目根目录 --->npm run debug:server

```

<div align=center>
<img src="/mybook/professional-yonbuilder/mdf/framework/images/6.png"/>
</div>
<p align="center">图 6</p>


