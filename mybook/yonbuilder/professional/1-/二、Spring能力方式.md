# 二、Spring能力方式



<a name="16cf570f"></a>
# 编写service

<br />**增加resoures文件**<br />![](https://cdn.nlark.com/yuque/0/2020/png/1431516/1599135773567-b8a0bb31-6d55-4f0f-baf8-7f9c1cc8bca7.png#align=left&display=inline&height=426&margin=%5Bobject%20Object%5D&originHeight=942&originWidth=1503&size=0&status=done&style=none&width=680)<br />图1<br />![](https://cdn.nlark.com/yuque/0/2020/png/1431516/1599135773644-9b744eac-89a1-4a0c-8e13-5dae683892a6.png#align=left&display=inline&height=457&margin=%5Bobject%20Object%5D&originHeight=889&originWidth=1323&size=0&status=done&style=none&width=680)<br />图2<br />
<br />**编写mybatis配置文件**<br />
<br />![](https://cdn.nlark.com/yuque/0/2020/png/1431516/1599135773687-75bb0e2a-4598-4754-ac09-ceca736d7397.png#align=left&display=inline&height=349&margin=%5Bobject%20Object%5D&originHeight=870&originWidth=1697&size=0&status=done&style=none&width=680)<br />图3<br />

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd">

<mapper namespace="com.yonyou.ucf.mdf.domain.dao.mybatisActivityDao">
    <select id="select" resultType="map">
        select code,name from  psndoc_zzd limit 10
    </select>
</mapper>
```

<br />**编写service**<br />
<br />![](https://cdn.nlark.com/yuque/0/2020/png/1431516/1599135773652-cc2d6477-0c25-4b4a-931b-92548e9c5471.png#align=left&display=inline&height=319&margin=%5Bobject%20Object%5D&originHeight=794&originWidth=1692&size=0&status=done&style=none&width=680)<br />图4<br />

```java
package com.yonyou.ucf.mdf.domain.service;

import com.yonyou.ucf.mdd.common.context.MddBaseContext;
import com.yonyou.ucf.mdd.core.dao.biz.IBizDataMapperDao;
import lombok.extern.slf4j.Slf4j;
import org.springframework.stereotype.Service;

import java.util.Map;

/**
 * mybatis方式操作数据库示例
 */
@Slf4j
@Service
public class MybatisActivityService {


    /**
     * 查询示例
     * @param params
     * @throws Exception
     * @return
     */
    public Object selectMybatis(Map<String, Object> params) throws Exception {
        Object obj = ((IBizDataMapperDao) MddBaseContext.getMapperDao(IBizDataMapperDao.class)).
                dynamicExecSelectSql("com.yonyou.ucf.mdf.domain.dao.mybatisActivityDao.select", null);
        return obj;
    }

}
```


<a name="41bd4d21"></a>
# 编写controller

<br />![](https://cdn.nlark.com/yuque/0/2020/jpeg/1431516/1599135773609-2c2bc5f2-d188-4186-afc3-26e52fbb6d03.jpeg#align=left&display=inline&height=366&margin=%5Bobject%20Object%5D&originHeight=894&originWidth=1663&size=0&status=done&style=none&width=680)<br />图5<br />

```java
package com.yonyou.ucf.mdf.app.controller.activity;

import com.yonyou.ucf.mdd.common.context.MddBaseContext;
import com.yonyou.ucf.mdd.common.dto.BaseReqDto;
import com.yonyou.ucf.mdd.common.interfaces.context.ISimpleUser;
import com.yonyou.ucf.mdf.app.common.ResultMessage;
import com.yonyou.ucf.mdf.app.controller.BillController;
import com.yonyou.ucf.mdf.domain.service.MddActivityService;
import com.yonyou.ucf.mdf.domain.service.MybatisActivityService;
import com.yonyou.ucf.mdf.domain.service.SqlActivityService;
import lombok.extern.slf4j.Slf4j;
import org.imeta.orm.base.BizObject;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.util.Map;

/**
 * @author nishch
 * @version 1.0
 * @date 2020/7/7
 * @des 活动管理控制器
 */
@Slf4j
@RestController
@RequestMapping("/activity")
public class ActivityController extends BillController {

    @Autowired
    MddActivityService mddActivityService;

    @Autowired
    MybatisActivityService mybatisActivityService;

    @Autowired
    SqlActivityService sqlActivityService;

    /**
     * 测试查询数据
     *
     * @param params
     * @param request
     * @param response
     */
    @RequestMapping("/select")
    public void getBill(@RequestBody BizObject params, HttpServletRequest request, HttpServletResponse response) {
        try {
            //获取当前登录用户信息
            ISimpleUser user = MddBaseContext.getCurrentUser();
            Object object2 = mybatisActivityService.selectMybatis(params);
            Object object3  = sqlActivityService.selectNoParams();
            this.renderJson(response, ResultMessage.data(object2));
        } catch (Exception e) {
            this.renderJson(response, ResultMessage.error(e.getMessage()));
        }
    }


    @RequestMapping("/update")
    public void update(@RequestBody BaseReqDto bill, HttpServletRequest request, HttpServletResponse response) {
        try {
            //可以在这里添加自己的逻辑bill
            super.save(bill, request, response);
            this.renderJson(response, ResultMessage.success());
        } catch (Exception e) {
            this.renderJson(response, ResultMessage.error(e.getMessage()));
        }
    }


}
```


<a name="a285W"></a>
# 自定义按钮
![](https://cdn.nlark.com/yuque/0/2020/jpeg/1431516/1599135773917-998a92ec-4ed0-486a-b417-8eb2db5d194b.jpeg#align=left&display=inline&height=318&margin=%5Bobject%20Object%5D&originHeight=854&originWidth=1825&size=0&status=done&style=none&width=680)<br />图6<br />

<a name="d7a484cb"></a>
# 编写前端函数

<br />![](https://cdn.nlark.com/yuque/0/2020/png/1431516/1599135773687-226eb54b-05db-442b-89ad-97cf473f735d.png#align=left&display=inline&height=282&margin=%5Bobject%20Object%5D&originHeight=783&originWidth=1888&size=0&status=done&style=none&width=680)<br />图7<br />![](https://cdn.nlark.com/yuque/0/2020/jpeg/1431516/1599135773589-e017aea8-eada-4bfa-8305-42b4ffb248bc.jpeg#align=left&display=inline&height=348&margin=%5Bobject%20Object%5D&originHeight=704&originWidth=1377&size=0&status=done&style=none&width=680)<br />图8<br />

```javascript
function (event) {
  var viewModel = this;
  viewModel.get('button7pa').on('click', function () {
    var proxy = cb.rest.DynamicProxy.create({
                settle: {
                    url: 'activity/select',
                    method: 'POST'
                }
            });
            proxy.settle(viewModel.getParams(), function(err, result) {
                if (err) {
                    cb.utils.alert(err.message, 'error');
                    return;
                }
                if (result != undefined) {
                    //对结果进行处理
                }
            });
  })
}
```


<a name="hFwh6"></a>
# 绑定函数
![](https://cdn.nlark.com/yuque/0/2020/jpeg/1431516/1599135773626-d70ee056-fed2-464a-8764-6dcf17e33efb.jpeg#align=left&display=inline&height=303&margin=%5Bobject%20Object%5D&originHeight=855&originWidth=1916&size=0&status=done&style=none&width=680)<br />图9
<a name="7ro1D"></a>
# 测试
![](https://cdn.nlark.com/yuque/0/2020/jpeg/1431516/1599135773609-7a0339e0-beb1-49c8-a791-778cc31e7824.jpeg#align=left&display=inline&height=329&margin=%5Bobject%20Object%5D&originHeight=912&originWidth=1883&size=0&status=done&style=none&width=680)<br />图10<br />![](https://cdn.nlark.com/yuque/0/2020/png/1431516/1599135773598-98203e00-8489-4086-893a-2c7930134e78.png#align=left&display=inline&height=264&margin=%5Bobject%20Object%5D&originHeight=736&originWidth=1898&size=0&status=done&style=none&width=680)<br />图11
