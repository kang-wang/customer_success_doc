# 应用构建标准版基本操作流程

进入大赛租户下点击应用构建服务->点击构建平台->点击应用构建

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/1.png"/>
</div>
<p align="center">图 1</p>

创建属于自己的应用：点击新建应用

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/2.png"/>
</div>
<p align="center">图 2</p>

下一步

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/3.png"/>
</div>
<p align="center">图 3</p>

填写应用名称、选择所属领域、选择应用图标-->最后点击完成。

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/4.png"/>
</div>
<p align="center">图 4</p>

创建成功后，会在界面上看到一个应用。

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/5.png"/>
</div>
<p align="center">图 5</p>

点击进入应用，会看到四大模块

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/6.png"/>
</div>
<p align="center">图 6</p>

<font  color=red >数据建模：</font>相当于平时使用的数据库，这里可以新建实体，查询，枚举。<br>
<font  color=red >页面建模：</font>把设计好的表生成页面展示出来，也可以生成报表、分析、以及嵌入第三方H5页面。<br>
<font  color=red >流程&自动化：</font>审批流，业务流，以及函数的编写都在这里。<br>
<font  color=red >发布管理：</font>就是把创建好的应用发布到菜单。<br>

<table>
<tr>
<td bgcolor=#CCFFFF>整个流程大概是：数据建模-->页面建模-->流程自动化（可选）-->发布管理<br>
 如不需要审批流，业务流，以及前后端函数编写，则跳过流程自动化这一步骤。
 </td>
 </tr>
</table>


<hr>

<h2> 数据建模</h2>

新增查询：做报表或者智能分析时涉及到多表查询时，要建立查询。<br>

新增枚举：在新建实体中，数据类型选择单选或者多选时可以用到，样式如下图所示

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/7.png"/>
</div>
<p align="center">图 7</p>

新增实体

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/8.png"/>
</div>
<p align="center">图 8</p>

<font  color=red >父实体：相当于数据库中的外键，可选择的只能是发布后的实体。</font><br>
<font  color=red >审批：</font>审批流相关操作，如需审批（工作）流必须勾选。<br>
<font  color=red >业务流：</font>业务流相关操作，如需业务流必须勾选。<br>
<font  color=red >交易类型：</font>生成单选引用，可以选择交易的类型<br>
<font  color=red >树形结构：</font>后续页面建模中树形表，左树右卡，左树右表，这些有关树的操作会用到。<br>
<font  color=red >自动编码：</font>会生成编码，自动编码。<br>
<font  color=red >档案状态：</font>会生成一个字段选项，启用、停用。<br>
<font  color=red >主组织：</font>生成字段，组织单元，会在页面上生成一个参照。<br>

<table>
<tr>
<td bgcolor=#CCFFFF>勾选相应接口之后，会在系统属性中生成相应字段，不用理会。
 </td>
 </tr>
</table>

点击到属性

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/9.png"/>
</div>
<p align="center">图 9</p>

根据自己的需要填写编码及名称。

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/10.png"/>
</div>
<p align="center">图 10</p>

<h3>  <font  color=red >注意：要做引用，或者树形页面，实体里必须要有name字段</font> </h3>

这里面的数据类型主要说一下单选、多选以及单选引用
<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/11.png"/>
</div>
<p align="center">图 11</p>



单选、多选：只能选择创建的枚举

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/12.png"/>
</div>
<p align="center">图 12</p>

单选引用：可以引用自己创建的实体和系统自带的。

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/13.png"/>
</div>
<p align="center">图 13</p>

<hr>

## 页面建模

新建页面

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/14.png"/>
</div>
<p align="center">图 14</p>

点击新建页面后可以看到

单据：可以看到单表、单卡、左树右表、左树右卡、一主多子、主子表、树形表

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/15.png"/>
</div>
<p align="center">图 15</p>

分析：分析、报表、分析卡片、引用已有

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/16.png"/>
</div>
<p align="center">图 16</p>

画布：当对之前的页面布局不满意时，可以自己设计布局

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/17.png"/>
</div>
<p align="center">图 17</p>

第三方：添加第三方H5页面

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/18.png"/>
</div>
<p align="center">图 18</p>

以单卡为例创建页面

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/19.png"/>
</div>
<p align="center">图 19</p>


<table>
<tr>
<td bgcolor=#CCFFFF>默认勾选生成列表，因为是先进入到列表，看到表内信息，再进行增删改的。
 </td>
 </tr>
</table>

参照：如本页面被其他后续页面引用，需生成参照。也可在参照里新增参照，最后发布。

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/20.png"/>
</div>
<p align="center">图 20</p>


<table>
<tr>
<td bgcolor=#CCFFFF>选择元数据，这里的元数据必须是发布后的实体才能看到。
 </td>
 </tr>
</table>


点击完成后，生成两个页面

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/21.png"/>
</div>
<p align="center">图 21</p>

点击设备大类进行编辑<br>
会根据自己创建的实体中的字段自动生成相应的控件

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/22.png"/>
</div>
<p align="center">图 22</p>

在界面的左边可以根据自己的需求拖拽添加控件

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/23.png"/>
</div>
<p align="center">图 23</p>

点击卡片中的控件可以删除和编辑控件具体操作


<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/24.png"/>
</div>
<p align="center">图 24</p>

可以进行属性配置和动作配置

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/25.png"/>
</div>
<p align="center">图 25</p>

动作配置可以添加自己编写的前后端函数

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/26.png"/>
</div>
<p align="center">图 26</p>

对保存按钮设置保存前校验规则

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/27.png"/>
</div>
<p align="center">图 27</p>

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/28.png"/>
</div>
<p align="center">图 28</p>


<table>
<tr>
<td bgcolor=#CCFFFF>一主多子页面：在新建实体中被引用为父实体的实体才能在元数据时找到。
 </td>
 </tr>
</table>

主子表样式:

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/29.png"/>
</div>
<p align="center">图 29</p>

<table>
<tr>
<td bgcolor=#CCFFFF>主子孙页面：主子孙类似于主子表。
 </td>
 </tr>
</table>

主子孙样式：

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/30.png"/>
</div>
<p align="center">图 30</p>

<table>
<tr>
<td bgcolor=#CCFFFF>左树右卡：只有在建立实体的时候，选择树形结构，才能在元数据中看到。
 </td>
 </tr>
</table>

左树右卡样式:

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/31.png"/>
</div>
<p align="center">图 31</p>

<table>
<tr>
<td bgcolor=#CCFFFF>左树右表：前提左边的树要建立好。先建立左树右卡，再建立左树右表
 </td>
 </tr>
</table>


<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/32.png"/>
</div>
<p align="center">图 32</p>

左树右表样式：


<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/33.png"/>
</div>
<p align="center">图 33</p>

树形表样式：

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/34.png"/>
</div>
<p align="center">图 34</p>

<hr>

## 流程&自动化

工作（审批）流：

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/35.png"/>
</div>
<p align="center">图 35</p>

点击相应目录->点击新增->填写审批流名称（随意填写）->点击确定

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/36.png"/>
</div>
<p align="center">图 36</p>

点击设计进入设计界面

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/37.png"/>
</div>
<p align="center">图 37</p>

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/38.png"/>
</div>
<p align="center">图 38</p>


<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/39.png"/>
</div>
<p align="center">图 39</p>

这里的配置是，节点名称：确认。参与人：发起人（勾选上发起人可以在测试的时候方便查看）。

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/40.png"/>
</div>
<p align="center">图 40</p>

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/41.png"/>
</div>
<p align="center">图 41</p>


<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/42.png"/>
</div>
<p align="center">图 42</p>


配置完成后点击保存并发布，就已经启用成功

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/43.png"/>
</div>
<p align="center">图 43</p>

在配置审批流的列表下填写数据未提交时是开立态

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/44.png"/>
</div>
<p align="center">图 44</p>

勾选想要提交的数据，提交，变为审核中，（审批人可在审批中心查看到提交的单据）
当设置的审批人审批同意后变为已审核


<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/45.png"/>
</div>
<p align="center">图 45</p>

<font  color=red >若初次打开审批中心，来源以及处理状态为空时，需要租户管理员预先添加对应应用（点击右上角设置即可）</font>

业务流：


<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/46.png"/>
</div>
<p align="center">图 46</p>


<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/47.png"/>
</div>
<p align="center">图 47</p>

根据自己需要填写相应的基本信息，触发设置，生单方式，转换规则以及分单规则

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/48.png"/>
</div>
<p align="center">图 48</p>

<table>
<tr>
<td bgcolor=#CCFFFF><b>审批流，业务流在开发者大赛第45课</b>
 </td>
 </tr>
</table>



<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/49.png"/>
</div>
<p align="center">图 49</p>

<table>
<tr>
<td bgcolor=#CCFFFF><b>函数入门在开发者大赛第46课</b>
 </td>
 </tr>
</table>


<hr>

## 发布管理

将应用发布,选择应用所在领域

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/50.png"/>
</div>
<p align="center">图 50</p>

如下图所示目录结构样例

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/51.png"/>
</div>
<p align="center">图 51</p>

发布成功后显示已发布

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/52.png"/>
</div>
<p align="center">图 52</p>

最后会生成如下图所示应用列表

<div align=center>
<img src="/mybook/yonbuilder/standard/1-/images/53.png"/>
</div>
<p align="center">图 53</p>




