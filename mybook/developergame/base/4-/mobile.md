# 移动能力
学习移动能力并使用前端函数对功能进行扩展

## 准备

###### 页面初始化

```
function (event) {
  console.log("ddd","hello");
  var viewModel = this;
  mtl.getLocation({
    type:'wgs84',//默认为wgs84的gps坐标，如果要返回直接给openLocation用的火星坐标，可传入'gcj02'
    success:function(res){
        console.log(JSON.stringify(res));
        viewModel.get("dangqianjingdu").setValue(res.longitude);
        viewModel.get("dangqianweidu").setValue(res.latitude);
        viewModel.get("dangqianweizhi").setValue(JSON.stringify(res));
        viewModel.get("1592392705119_74").setValue(res.address);
        var latitude = res.latitude;//纬度，浮点数，范围为90~-90
        var longitude = res.longitude;//经度，浮点数，范围为180~-180。
    },
    fail(err) {
        console.log(JSON.stringify(err));
        viewModel.get("1592392705119_74").setValue("获得定位失败："+err.message);
        // alert(err.message);
    }
  });
} 

```

#### 操作流程

1. 新增设备巡检移动端列表、卡片
2. 在移动端列表设置关联卡片（如果创建单据时勾选了移动，则会自动关联）
3. 调整列表页面，调整查询方案
4. 调整卡片界面显示，注意配置参照。
5. 巡检执行和设备巡检操作相似，创建、调整布局即可
6. 创建巡检执行初始化函数。点击巡检执行移动卡片，进入设计器，点击初始化，绑定函数
7. 发布应用，将要发布的页面添加进入分组列表。点击发布应用，勾选友空间，选择应用类别，点击确定即可。
8. 打开移动端测试