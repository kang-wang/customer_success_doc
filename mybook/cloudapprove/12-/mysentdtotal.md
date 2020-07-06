## 获取发起事项统计
获取发起事项统计
- - -
#### URL ####
https://ys.yonyoucloud.com/ubpm-web-rest/service/query/ext/historic-process-instances/count

- - - 
#### 支持格式 ####
JSON
- - - 
#### HTTP请求方式 ####
POST
- - - 
#### HEADER参数 ####

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="200px">Content-Type</td>
        <td width="300px">application/json;charset=UTF-8</td>
    </tr>
    <tr align="center">
        <td>restservice</td>
        <td>REST_SERVICE_1.0.0</td>
    </tr>
    <tr align="center">
        <td>cache-control</td>
        <td>no-cache</td>
    </tr>
    <tr align="center">
        <td>source</td>
        <td>approve</td>
    </tr>
    <tr align="center">
        <td>tenant</td>
        <td>租户id,请看注意事项</td>
    </tr>
    <tr align="center">
        <td>securitytenant</td>
        <td>租户id,请看注意事项</td>
    </tr>
    <tr align="center">
        <td>sign</td>
        <td>认证字符串--后端加密算法生成的,根据请求token+url+tenant，具体获取请看注意事项</td>
    </tr>
</table>

#### 请求参数 ####
- - - 

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="100px"></td>
        <td width="100px">必选</td>
        <td width="150px">类型及范围</td>
        <td width="200px">说明</td>
    </tr>
    <tr align="center">
        <td>finished</td>
        <td>false</td>
        <td>boolean</td>
        <td>是否流程结束</td>
    </tr>
    <tr align="center">
        <td>startedBy</td>
        <td>true</td>
        <td>string</td>
        <td>发起人友互通id</td>
    </tr>
</table>

- - - 
#### 请求JSON数据 ####
```
{
	"finished": false,
	"startedBy": "0f059088-9c92-4769-a3e7-8f1a341cc3df"
}
```
---

#### 返回结果 ####

```
{
	"instancesCount": 11
}

```
- - - 

#### 注意事项 ####

- 获取租户id:

<div align=center>
<img src="/mybook/cloudapprove/2-/images/1.png"/>
</div>
<p align="center">图 1</p>

- 获取sign

#### 第一步：下载测试Demo

代码Demo git地址[链接](https://github.com/YYETST/cloud-approve.git)

#### 第二步：配置application.properties

如何配置请查看文档[权限验证](/mybook/cloudapprove/2-/Identity_verify.md)

#### 第三步：加载云审批jar包到项目中

src/main/resources/lib

#### 获取sign

一个接口调用一次就可以了
url不变，租户id不变，sign是不会变的,
在接口中写死就可以了

SignTest.getMySendTotal()
在方法内部填写自己请求的url即可获取到sign