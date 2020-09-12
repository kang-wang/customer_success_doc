## 标准版常见问题

### 问题：YonBuilder标准服务入口在哪里

<div align=center>
<img src="/mybook/yonbuilder/generallink/8-/images/5.png"/>
</div>
<p align="center">图 1</p>

### 问题：YonBuilder产品是否支持私有化部署？

支持

### 问题：YonBuilder、YonBIP、YonSuite三者之间的关系

<div align=center>
<img width="800px" src="/mybook/yonbuilder/generallink/8-/images/9.jpg"/>
</div>
<p align="center">图 1</p>

### 问题：修改了实体后，页面上怎么显示修改的字段

点击控件，点击字段设置，进行拖拽即可

<div align=center>
<img src="/mybook/yonbuilder/generallink/8-/images/2.png"/>
</div>
<p align="center">图 2</p>

<div align=center>
<img src="/mybook/yonbuilder/generallink/8-/images/3.png"/>
</div>
<p align="center">图 3</p>

### 问题：报cCardKey不存在错误？ 

目前不支持单表，如果需要的话，请创建单卡。

<div align=center>
<img src="/mybook/yonbuilder/generallink/8-/images/1.png"/>
</div>
<p align="center">图 4</p>

### 问题：系统预制的按钮，没办法写前端函数？ 

请通过页面初始化编写 (beforeAction等等)

<div align=center>
<img src="/mybook/yonbuilder/generallink/8-/images/4.png"/>
</div>
<p align="center">图 5</p>

### 问题：发现一些按钮没有规则链，是怎么回事？

<h4>系统本身有些按钮是没有预制规则链的</h4>

### 问题：发布后在菜单看不到自己的应用怎么办？

<div align=center>
<img src="/mybook/yonbuilder/generallink/8-/images/6.png"/>
</div>
<p align="center">图 6</p>

<div align=center>
<img src="/mybook/yonbuilder/generallink/8-/images/7.png"/>
</div>
<p align="center">图 7</p>


### 问题：新建查询时，枚举型字段怎么获取名称？

目前是在分析卡片里加自定义字段写公式实现if(sex==1,"男","女")。

<div align=center>
<img src="/mybook/yonbuilder/generallink/8-/images/8.png"/>
</div>
<p align="center">图 8</p>

<div align=center>
<img src="/mybook/yonbuilder/generallink/8-/images/12.png"/>
</div>
<p align="center">图 12</p>

### 问题：数据库表不存在

原因：数据库中并未存在该表
<div align=center>
<img src="/mybook/yonbuilder/generallink/8-/images/10.png"/>
</div>
<p align="center">图 10</p>

解决方案：在数据建模选中批量导出sql，在数据库执行sql脚本即可

<div align=center>
<img src="/mybook/yonbuilder/generallink/8-/images/11.png"/>
</div>
<p align="center">图 11</p>

### 问题：获取实体失败,id:3a59b048-fce0-4afd-9a17-6698457329e4,tenantId:wae39i63
一个星期内，实体存在删除，导致页面与实体对应不上，一周后服务器缓存清除导致报错

### 问题：获取参照元数据失败：1010001100017；
联系开发人员，需要升级脚手架

### 问题：应用构建中数据建模导出sql 导出的文件是0kb
实体存在错误的单选、单选引用等关系，需要检查实体。











