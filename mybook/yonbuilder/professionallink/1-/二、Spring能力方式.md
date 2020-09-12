# 二、Spring能力方式


# 编写service

<br />**增加resoures文件**<br />

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/spring/1.png"/>
</div>
<p align="center">图 1</p>

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/spring/2.png"/>
</div>
<p align="center">图 2</p>

<br />**编写mybatis配置文件**<br />

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/spring/3.png"/>
</div>
<p align="center">图 3</p>

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

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/spring/4.png"/>
</div>
<p align="center">图 4</p>

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


# 编写controller

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/spring/5.jpeg"/>
</div>
<p align="center">图 5</p>

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



# 自定义按钮

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/spring/6.jpeg"/>
</div>
<p align="center">图 6</p>

# 编写前端函数

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/spring/7.png"/>
</div>
<p align="center">图 7</p>

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/spring/8.jpeg"/>
</div>
<p align="center">图 8</p>

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



# 绑定函数

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/spring/9.jpeg"/>
</div>
<p align="center">图 9</p>

# 测试

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/spring/10.jpeg"/>
</div>
<p align="center">图 10</p>

<div align=center>
<img src="/mybook/yonbuilder/professionallink/1-/images/spring/11.png"/>
</div>
<p align="center">图 11</p>
