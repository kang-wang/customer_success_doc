# 人员信息维护

## 准备资料

#### 枚举

###### 性别

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="200px">名称：</td>
        <td width="300px" colspan="2">性别</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="2">gender</td>
    </tr>
    <tr align="center">
        <td>类型：</td>
        <td colspan="2">字符</td>
    </tr>
    <tr align="center">
        <td>枚举内容：</td>
        <td>枚举值</td>
        <td>名称</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>1</td>
        <td>男</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>0</td>
        <td>女</td>
    </tr>
</table>

###### 任职状态

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="200px">名称：</td>
        <td width="300px" colspan="2">任职状态</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="2">work_state</td>
    </tr>
    <tr align="center">
        <td>类型：</td>
        <td colspan="2">字符</td>
    </tr>
    <tr align="center">
        <td>枚举内容：</td>
        <td>枚举值</td>
        <td>名称</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>1</td>
        <td>在职</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>2</td>
        <td>离职</td>
    </tr>
</table>

#### 实体

###### 人员信息

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="500px" colspan="4">人员信息</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="4">bd_psndoc</td>
    </tr>
    <tr align="center">
        <td>父实体：</td>
        <td colspan="4"></td>
    </tr>
    <tr align="center">
        <td>引用接口：</td>
        <td colspan="4"></td>
    </tr>
    <tr align="center">
        <td>属性：</td>
        <td>编码</td>
        <td>名称</td>
        <td>类型</td>
        <td>引用</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>name</td>
        <td>姓名</td>
        <td>文本</td>
        <td></td>
    </tr>
        <tr align="center">
                <td></td>
                <td>age</td>
                <td>年龄</td>
                <td>整数</td>
                <td></td>
            </tr>
            <tr align="center">
                    <td></td>
                    <td>gender</td>
                    <td>性别</td>
                    <td>单选</td>
                    <td>性别</td>
                </tr>
                <tr align="center">
                                <td></td>
                                <td>mobile</td>
                                <td>手机</td>
                                <td>联系方式</td>
                                <td></td>
                            </tr>
                            <tr align="center">
                                            <td></td>
                                            <td>email</td>
                                            <td>邮箱</td>
                                            <td>文本</td>
                                            <td></td>
                                        </tr>
</table>


###### 任职记录

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="500px" colspan="4">任职记录</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="4">work_record</td>
    </tr>
    <tr align="center">
        <td>父实体：</td>
        <td colspan="4">人员信息</td>
    </tr>
    <tr align="center">
        <td>引用接口：</td>
        <td colspan="4"></td>
    </tr>
    <tr align="center">
        <td>属性：</td>
        <td>编码</td>
        <td>名称</td>
        <td>类型</td>
        <td>引用</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>company</td>
        <td>公司</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>begindate</td>
        <td>开始日期</td>
        <td>日期</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>enddate</td>
        <td>结束日期</td>
        <td>日期</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>reason</td>
        <td>离职原因</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
            <td></td>
            <td>state</td>
            <td>状态</td>
            <td>单选</td>
            <td>任职状态</td>
        </tr>
</table>


###### 培训经历

<table border="1" cellpadding="3" cellspaing="3">
    <tr align="center">
        <td width="120px">名称：</td>
        <td width="500px" colspan="4">培训经历</td>
    </tr>
    <tr align="center">
        <td>编码：</td>
        <td colspan="4">trained_experience</td>
    </tr>
    <tr align="center">
        <td>父实体：</td>
        <td colspan="4">人员信息</td>
    </tr>
    <tr align="center">
        <td>引用接口：</td>
        <td colspan="4"></td>
    </tr>
    <tr align="center">
        <td>属性：</td>
        <td>编码</td>
        <td>名称</td>
        <td>类型</td>
        <td>引用</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>org</td>
        <td>机构</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>begindate</td>
        <td>开始时间</td>
        <td>日期</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>enddate</td>
        <td>结束时间</td>
        <td>日期</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>content</td>
        <td>培训内容</td>
        <td>文本</td>
        <td></td>
    </tr>
    <tr align="center">
        <td></td>
        <td>result</td>
        <td>成果</td>
        <td>文本</td>
        <td></td>
    </tr>
</table>

## 操作流程

1. 新建页面一主多子
2. 列表界面调整布局:姓名取消链接查询

<div align=center>
<img src="/mybook/developergame/professional/4-/images/1.png"/>
</div>
<p align="center">图 1</p>

<div align=center>
<img src="/mybook/developergame/professional/4-/images/2.png"/>
</div>
<p align="center">图 2</p>


## 专业版任务卡片

####  前端函数
1. 校验邮箱

```
function (event) {
  var viewModel = this;
  viewModel.get('email').on('afterValueChange',
  function (data) {
    const validateEmail = str =>
    /^(([^<>()\[\]\.,;:\s@"]+(\.[^<>()\[\]\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/.test(str);
    if(!validateEmail(data.value)){
    cb.utils.alert('邮箱格式错误');
  }
  });
}

```

####  后端规则

1. 任职记录保存前校验子集不能为空
2. 任职记录保存前校验结束时间大于开始时间
3. 任职记录没有结束时间的不允许删除
4. 列表界面启用不允许删除

- 示例

```
import com.yonyou.ucf.mdd.common.model.rule.RuleContext;
import com.yonyou.ucf.mdd.common.model.rule.RuleExecuteResult;
import com.yonyou.ucf.mdd.common.model.uimeta.UIMetaBaseInfo;
import com.yonyou.ucf.mdd.rule.base.AbstractRule;
import com.yonyou.ucf.mdf.app.exceptions.BusinessException;
import org.imeta.orm.base.BizObject;
import org.springframework.stereotype.Component;

import java.util.*;

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
        //获取UI元数据
        UIMetaBaseInfo uiMetaBaseInfo = ruleContext.getUiMetaBaseInfo();
        //取业务数据
        List<BizObject> bizObjectList = this.getBizObjects(uiMetaBaseInfo, ruleContext);
        Iterator var6 = bizObjectList.iterator();
        while(var6.hasNext()) {
            BizObject bizObject = (BizObject)var6.next();
            if(null==bizObject.get("work_recordList")||((List)bizObject.get("work_recordList")).size()==0){
                throw  new BusinessException("任职记录必须有数据哦");
            }
        }
        return new RuleExecuteResult();
    }
}


```

