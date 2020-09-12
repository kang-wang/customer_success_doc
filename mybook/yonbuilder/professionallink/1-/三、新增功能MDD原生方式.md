# 三、新增功能MDD原生方式


## 一、编写规则
（和系统预制功能扩展方式规则相同，可跳过第一节）<br />

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/add/1.jpeg"/>
</div>
<p align="center">图 1</p>

### 规则一


```java
package com.yonyou.ucf.mdf.domain.rules;

import com.yonyou.ucf.mdd.common.interfaces.context.ISimpleUser;
import com.yonyou.ucf.mdd.common.model.rule.RuleContext;
import com.yonyou.ucf.mdd.common.model.rule.RuleExecuteResult;
import com.yonyou.ucf.mdd.common.model.uimeta.UIMetaBaseInfo;
import com.yonyou.ucf.mdd.rule.base.AbstractRule;
import com.yonyou.ucf.mdf.app.exceptions.BusinessException;
import com.yonyou.ucf.mdf.domain.util.CommonUtil;
import org.imeta.orm.base.BizObject;
import org.springframework.stereotype.Component;

import java.util.Iterator;
import java.util.List;

/**
 * @author nishch
 * @version 1.0
 * @date 2020/4/14
 * @des
 */
@Component("activityRule")
public class ActivityRule extends AbstractRule {



    @Override
    public <T> RuleExecuteResult execute(RuleContext ruleContext, T... tObjs) throws Exception {
        //获取当前用户信息
        ISimpleUser user = CommonUtil.getCurrentUser();
        //获取UI元数据
        UIMetaBaseInfo uiMetaBaseInfo = ruleContext.getUiMetaBaseInfo();
        //取业务数据
        List<BizObject> bizObjectList = this.getBizObjects(uiMetaBaseInfo, ruleContext);
        Iterator var6 = bizObjectList.iterator();
        while(var6.hasNext()) {
            BizObject bizObject = (BizObject)var6.next();
            if(null==bizObject.get("name")){
                throw  new BusinessException("不能为空");
            }
        }
        //规则间数据传递
        ruleContext.setCusMapValue("mycontent","12345");
        return new RuleExecuteResult();
    }
}
```


### 规则二

MddActivityService 请查看MDD操作数据库

```java
package com.yonyou.ucf.mdf.domain.rules;

import com.yonyou.ucf.mdd.common.model.rule.RuleContext;
import com.yonyou.ucf.mdd.common.model.rule.RuleExecuteResult;
import com.yonyou.ucf.mdd.common.model.uimeta.UIMetaBaseInfo;
import com.yonyou.ucf.mdd.rule.base.AbstractRule;
import com.yonyou.ucf.mdf.domain.service.MddActivityService;
import org.imeta.orm.base.BizObject;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Component;
import org.springframework.stereotype.Service;

import java.util.List;

/**
 * @author nishch
 * @version 1.0
 * @date 2020/4/14
 * @des
 */
@Component("activityRule2")
public class ActivityRule2 extends AbstractRule {


    @Autowired
    MddActivityService mddActivityService;

    @Override
    public <T> RuleExecuteResult execute(RuleContext ruleContext, T... tObjs) throws Exception {
        //获取上个规则设置的值
        String preRule =ruleContext.getCusMapValue("mycontent").toString();
        System.out.println(preRule);
        //调用数据库操作
        UIMetaBaseInfo uiMetaBaseInfo = ruleContext.getUiMetaBaseInfo();
        //获取实体
        List<BizObject> bizObjectList = this.getBizObjects(uiMetaBaseInfo, ruleContext);
        BizObject bizObject = bizObjectList.get(0);
        mddActivityService.select(bizObject);
        return new RuleExecuteResult();
    }
}
```


## 二、新增命令

- 点击命令管理

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/add/2.png"/>
</div>
<p align="center">图 2</p>
- 点击添加

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/add/3.png"/>
</div>
<p align="center">图 3</p>

- 根据提示填写相关信息（编码，名称等根据自己的业务需求写即可。）

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/add/4.png"/>
</div>
<p align="center">图 4</p>

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/add/5.png"/>
</div>
<p align="center">图 5</p>

- 点击确定

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/add/6.png"/>
</div>
<p align="center">图 6</p>

- 再点击进来可以看到系统自动生成了请求地址

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/add/7.png"/>
</div>
<p align="center">图 7</p>

## 三、新增按钮

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/add/8.png"/>
</div>
<p align="center">图 8</p>

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/add/9.png"/>
</div>
<p align="center">图 9</p>

## 四、绑定命令

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/add/10.png"/>
</div>
<p align="center">图 10</p>

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/add/11.png"/>
</div>
<p align="center">图 11</p>

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/add/12.png"/>
</div>
<p align="center">图 12</p>

## 五、验证

### 请求入口

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/add/13.png"/>
</div>
<p align="center">图 13</p>