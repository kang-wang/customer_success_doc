## 获取发起事项统计

- - -
#### 版本 ####
v1
- - -
#### SDK方法 ####
HistoryService.getHistoricProcessInstancesCount(HistoricProcessInstancesQueryParam queryParam)
- - - 
#### 请求参数 ####

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="100px"></td>
        <td width="100px">必选</td>
        <td width="150px">类型及范围</td>
        <td width="200px">说明</td>
    </tr>
    <tr align="center">
        <td>yhtuserid</td>
        <td>true</td>
        <td>string</td>
        <td>友互通userid</td>
    </tr>
</table>

- - - 
#### 请求数据 ####
```
{
	"startedBy": "0f059088-9c92-4769-a3e7-8f1a341cc3df",
}
```
---

#### 返回结果 ####

```

{"instancesCount":14}

```
- - - 
#### 返回字段说明 ####

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="100px">返回值字段</td>
        <td width="80px">字段类型</td>
        <td width="200px">字段说明</td>
    </tr>
    <tr align="center">
        <td>instancesCount</td>
        <td>int</td>
        <td>发起数量</td>
    </tr>
</table>


###### 如何获取yhtuserid

请使用自建应用接入文档，然后根据手机号获取用的yhtuserid

[自建接入](mybook/selfbuild/README.md)

###### 测试类

FlowTest.getMySendTotal()