# 附录：MDD操作数据库



<a name="56ddc8a6"></a>
# 方式一


```java
package com.yonyou.ucf.mdf.domain.service;

import com.yonyou.ucf.mdd.core.meta.MddMetaDaoHelper;
import com.yonyou.ucf.mdd.core.utils.UIMetaHelper;
import lombok.extern.slf4j.Slf4j;
import org.imeta.orm.base.BizObject;
import org.imeta.orm.schema.QueryCondition;
import org.imeta.orm.schema.QueryConditionGroup;
import org.imeta.orm.schema.QuerySchema;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import java.util.List;
import java.util.Map;

/**
 * mdd方式操作数据库示例
 */
@Slf4j
@Service
public class MddActivityService {

    @Autowired
    MddMetaDaoHelper mddMetaDaoHelper;

    /**
     * 简单查询
     * @throws Exception
     */
    public List<Map<String,Object>> select(BizObject bizObject) throws Exception{
        //情况一
        QueryConditionGroup queryConditionGroup = QueryConditionGroup.and(
                QueryCondition.name("name").eq(bizObject.get("name"))
        );
        QuerySchema schema = QuerySchema.create().addSelect("code,name,count").addCondition(queryConditionGroup)
                .addOrderBy("count");
        //情况二
//        QuerySchema schema=QuerySchema.create()
//                .addSelect("code,name,type")
//                .appendQueryCondition(
//                        QueryConditionGroup.and(Query=Condition.name("name").eq(params.get("name"))),
//                        QueryConditionGroup.and(QueryCondition.name("beforeDate").elt(params.get("beforeDate"))),
//                        QueryConditionGroup.and(QueryCondition.name("afterDate").egt(params.get("afterDate")))
//                );
        //实体类名--fullname即实体的URL
        //List<Map<String,Object>> results = mddMetaDaoHelper.query("GT1190AT5.GT1190AT5.activity_doc", schema);
        //也可以使用这种方式操作
        List<Map<String,Object>> results = UIMetaHelper.mddMetaDaoHelp().query("GT9721AT52.GT9721AT52.psndoc_zzd", schema);
        return results;
    }

}
```

<br />

