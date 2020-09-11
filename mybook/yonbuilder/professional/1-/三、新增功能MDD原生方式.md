# 三、新增功能MDD原生方式

<a name="5mPi7"></a>
## 一、编写规则
（和系统预制功能扩展方式规则相同，可跳过第一节）<br />
<br />![](https://cdn.nlark.com/yuque/0/2020/jpeg/1431516/1599135486348-80dfbe8d-a134-47ac-8282-5c6ba58af3d5.jpeg#align=left&display=inline&height=387&margin=%5Bobject%20Object%5D&originHeight=860&originWidth=1512&size=0&status=done&style=none&width=680)<br />图1<br />

<a name="Pfi0N"></a>
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


<a name="qYbRr"></a>
### 规则二


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


<a name="aAhyI"></a>
## 二、新增命令

- 点击命令管理

![4.png](https://cdn.nlark.com/yuque/0/2020/png/1431516/1599140683474-01e5f7ef-1d87-42a1-9924-370294f4b399.png#align=left&display=inline&height=862&margin=%5Bobject%20Object%5D&name=4.png&originHeight=862&originWidth=1890&size=72893&status=done&style=none&width=1890)

- 点击添加

![5.png](https://cdn.nlark.com/yuque/0/2020/png/1431516/1599140715114-9477f648-3448-4f8c-a3a5-93ec1373195f.png#align=left&display=inline&height=886&margin=%5Bobject%20Object%5D&name=5.png&originHeight=886&originWidth=1745&size=136128&status=done&style=none&width=1745)

- 根据提示填写相关信息（编码，名称等根据自己的业务需求写即可。）

规则就是注解中自己填写的类名<br />![](https://cdn.nlark.com/yuque/0/2020/png/1431516/1599135486355-4c77b631-8e87-4926-b419-2b50d007d8e7.png#align=left&display=inline&height=267&margin=%5Bobject%20Object%5D&originHeight=566&originWidth=1442&size=0&status=done&style=none&width=680)<br />![6.png](https://cdn.nlark.com/yuque/0/2020/png/1431516/1599140727062-61f2121a-7835-4845-91fd-3bdb7415b629.png#align=left&display=inline&height=874&margin=%5Bobject%20Object%5D&name=6.png&originHeight=874&originWidth=1809&size=135230&status=done&style=none&width=1809)

- 点击确定

![7.png](https://cdn.nlark.com/yuque/0/2020/png/1431516/1599141004078-2e6c4a33-72c9-470f-86f0-a4f258564c30.png#align=left&display=inline&height=922&margin=%5Bobject%20Object%5D&name=7.png&originHeight=922&originWidth=1519&size=95817&status=done&style=none&width=1519)

- 再点击进来可以看到系统自动生成了请求地址

![14.png](https://cdn.nlark.com/yuque/0/2020/png/1431516/1599143132358-541d6d59-dfa8-4242-acea-eff9e84cb7c1.png#align=left&display=inline&height=877&margin=%5Bobject%20Object%5D&name=14.png&originHeight=877&originWidth=1313&size=88809&status=done&style=none&width=1313)
<a name="Gr9gJ"></a>
## 三、新增按钮
![1.png](https://cdn.nlark.com/yuque/0/2020/png/1431516/1599141085312-8b9bd731-6fb5-440a-8d93-f3f7cb05ea11.png#align=left&display=inline&height=824&margin=%5Bobject%20Object%5D&name=1.png&originHeight=824&originWidth=1871&size=112135&status=done&style=none&width=1871)<br />![2.png](https://cdn.nlark.com/yuque/0/2020/png/1431516/1599141102695-cb52f659-3ea8-48de-a530-62e390dac3f6.png#align=left&display=inline&height=813&margin=%5Bobject%20Object%5D&name=2.png&originHeight=813&originWidth=1794&size=72830&status=done&style=none&width=1794)
<a name="ubMc0"></a>
## 四、绑定命令
![3.png](https://cdn.nlark.com/yuque/0/2020/png/1431516/1599141113733-32de92d2-43a7-4399-97a6-0ea3bac0f325.png#align=left&display=inline&height=846&margin=%5Bobject%20Object%5D&name=3.png&originHeight=846&originWidth=1895&size=124568&status=done&style=none&width=1895)<br />
<br />![10.png](https://cdn.nlark.com/yuque/0/2020/png/1431516/1599141133213-9c9f7c90-63e7-4db8-be0e-a1e695be3ea8.png#align=left&display=inline&height=786&margin=%5Bobject%20Object%5D&name=10.png&originHeight=786&originWidth=1603&size=55663&status=done&style=none&width=1603)<br />
<br />![11.png](https://cdn.nlark.com/yuque/0/2020/png/1431516/1599141147346-15f5c6ba-9ccf-482c-803c-94329ae0c5fb.png#align=left&display=inline&height=731&margin=%5Bobject%20Object%5D&name=11.png&originHeight=731&originWidth=1593&size=106263&status=done&style=none&width=1593)
<a name="p7Eit"></a>
## 五、验证
<a name="mCNYl"></a>
### 请求入口
![13.png](https://cdn.nlark.com/yuque/0/2020/png/1431516/1599141417336-799c4255-26ba-4059-93a1-99a060e12a37.png#align=left&display=inline&height=770&margin=%5Bobject%20Object%5D&name=13.png&originHeight=770&originWidth=1492&size=95384&status=done&style=none&width=1492)
