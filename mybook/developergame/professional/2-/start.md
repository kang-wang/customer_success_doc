# MDD后端

## 课程内容

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="200px">原有功能通过RULE进行扩展</td>
    </tr>
    <tr align="center">
        <td width="200px">新增功能</td>
    </tr>
    <tr align="center">
         <td width="200px">常见调试</td>
     </tr>
</table>

#### 原有功能通过RULE进行扩展

- 后端添加Rule，继承com.yonyou.ucf.mdd.rule.base.AbstractRule
- 规则间数据传递ruleContext.setCusMapValue()
- 规则这里一般写查询、校验参数即可
- 卡片界面保存按钮增加Rule
- 校验规则

#### 新增功能

--- 

- 新增功能（按钮）
- 前端配置规则链，复用按钮中的某些规则
- 添加自定义的规则链

---
- 讲解后端目录结构: app\domain
- 增加controller
- 简介mdd方式操作数据库:MddActivityService
```
注解方式：MddMetaDaoHelper  
直接使用：UIMetaHelper.mddMetaDaoHelp()
```

#### 常见调试

- BillController  常见功能的入口controller
- RuleEngine.execute()
