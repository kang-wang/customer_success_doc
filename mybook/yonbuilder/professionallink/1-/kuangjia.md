# MDD框架介绍


## 一、功能概述
MDD（Model Driven Development），模型驱动开发，是一种企业开发常用的开发模式， 主要通过使用高度抽象的领域业务模型作为构件，完成代码转换实现或各种模型驱动引擎配 置支撑，降低开发成本，应对复杂需求变更。 <br />MDD 开发框架，是用友云针对企业数字化中台理念实现的一套开发框架。从企业云服 务核心问题域出发，总结提炼出最佳实践，且形成了统一的标准及规约。致力于支撑中台能力快速孵化，形成中台各能力间连接的纽带，最终实现中台基础上的企业数字化业务重构及创新快速开发实现。 <br />框架的主要目的实现模型和技术框架的分离，系统的业务部分和技术部分都可以各自进化而互不影响，让开发者更专注业务，并能够让初级的研发人员快速的开发出复杂的业务功能，其余由框架来封装屏蔽技术细节，降低技术难度，从而节省人力成本，缩短项目周期，提高软件安全质量。 <br />同时通过各种业务模型沉淀，也能为实现企业实现业务的技术积累，有助于企业业务分析。

## 二、MDD 开发框架架构概述

### 2.1、功能架构 

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/kuangjia/1.png"/>
</div>
<p align="center">图 1</p>

### 2.2、框架模块说明

| 模块 | 依赖模块 | 功能描述 |
| --- | --- | --- |
| mdd-basemeta-resources | - | 公共基础元数据xml  jar |
| mdd-basic | - | 基础接口及 model |
| mdd-common | mdd-basic | 基础模型 Util工具等; 接入 ucf-core 异常 |
| mdd-core | mdd-common,mdd-rpc, <br />mdd-redis-support | 核心公共处理逻辑; 接ucf-log |
| mdd-dao | mdd-uimeta-sdk | 数据操作 orm 接入模块 |
| mdd-redis-support | - | Redis 配置模块 |
| mdd-rpc | mdd-common | RPC 调用支持模块 |
| mdd-rule-sdk | mdd-core | 规则引擎 SDK |
| mdd-uimeta-design | mdd-dao | 模板设计器支持模块 |
| mdd-uimeta-sdk | mdd-rule-sdk | UI 元数据引擎 SDK |
| mdd-uretail-support | mdd-common, mdd-rpc | RPC 调用零售服务端兼容包 |
| mdd-default-rules | mdd-uimeta-sdk | 默认规则 |
| mdd-test-start | mdd-uimeta-sdk, <br />mdd-dao, <br />mdd-default-rules | 简单的 springboot 启动测试模块<br /> |




### 2.3、MDD驱动模块说明

| 模块 | 依赖模块 | 功能描述 |
| --- | --- | --- |
| ucf-mdf-api | - | 对外服务层 |
| ucf-mdf-app | ucf-mdf-domain<br />ucf-mdf-conf | 应用层 |
| ucf-mdf-bootstrap | ucf-mdf-app | 脚手架启动模块 |
| ucf-mdf-domain | - | 领域模块 |
| ucf-mdf-conf | - | 配置模块 |
| ucf-mdf-tools | ucf-mdf-conf | 工具模块，包含生成建表语句模型实体等功能 |


## 三、规则链

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/kuangjia/2.png"/>
</div>
<p align="center">图 2</p>

### 3.1、概述
动作规则即页面某按钮触发点击动作时，后端服务所执行的逻辑合集，最小单位称为规则，合集称为某动作的规则链。 <br />什么叫规则，说白了就是通过从规则注册表中查询到规则 ID（字符串），并当作 BeanName 获取到 Spring 注册的 service,并通过接口方法调用 execute 方法来执行一段逻辑获取最终结果。<br />

### 3.2、规则分层
规则总的分层分为系统级和租户级，每一级分层下又分为通用级、模块 级和单据级。系统和租户分层区分在于注册表中租户 ID 字段。 下一级分层 区分 billnum 字段。<br />目前YonBuilder客开的方式只支持单据级<br />

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/kuangjia/3.png"/>
</div>
<p align="center">图 3</p>

### 3.2、系统预制默认规则

- **mdd-default-rules包**

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/kuangjia/4.png"/>
</div>
<p align="center">图 4</p>

## 四、系统预制功能Controller

- **mdd-web包**
   - AlmightyController客开功能入口
   - BillController系统预制的增删查改入口

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/kuangjia/5.png"/>
</div>
<p align="center">图 5</p>