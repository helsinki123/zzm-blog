# vue3 使用百度map
```
index.html
 <script type="text/javascript" src="https://api.map.baidu.com/api?v=1.0&type=webgl&ak=Vx1FENzmVdeo2keYGuuVOb4tGsd2sGk3">
 </script>
 
 template
<div id="aaa"></div>


```
# js注意要写在onMounted
``` 
 var map = new BMapGL.Map("aaa");
// 创建地图实例 
var point = new BMapGL.Point(116.404, 39.915);
// 创建点坐标 
map.centerAndZoom(point, 15);
```

# bmap使用echarts的option格式
```
var option = {
    tooltip : {
        trigger: 'item'
    },
    bmap: {
        roam: true,//必填
        silent:true，
        zoom:数字,
        center:[展示中心位置],
        mapStyle:{
      
        }
        },
    series: 参照echarts格式
    
}
```
```
1. 安装echarts(使用3.x, 4.x版本)
npm install echarts@3.0.0 --save

如果需要在线定制适合自己项目的echarts包，可以使用<script>引入。建议开发环境使用echarts.js

<script src="echarts.min.js"></script>

在调用echarts的组件内引入，也可以在mian.js里面全局引入 import echarts from 'echarts'

如果项目使用typescript， 需要npm install @types/echarts --save

ECharts 目前暂停地图下载，所以使用百度地图作为底图，需要安装百度地图扩展

2. 安装百度地图扩展
bmap.js 下载地址https://github.com/apache/incubator-echarts/tree/master/extension/bmap

如果安装的是echarts完整包，里面包含百度地图扩展，路径为 echarts/extension/bmap/bmap.js

在项目里引入:

import 'echarts/extension/bmap/bmap' 或者 <script src="dist/extension/bmap.min.js"></script>

3. 引入百度地图jssdk
使用百度地图JavaScript API，需要先注册申请秘钥： http://lbsyun.baidu.com/apiconsole/key/create

<script type="text/javascript" src="http://api.map.baidu.com/api?v=3.0&ak=秘钥"></script>
百度地图的个性地图支持用户使用JavaScript API设置地图底图的样式风格以及控制组成地图底图的元素类的显示和隐藏。可以在个性化编辑平台定制适合自己项目的地图。编辑生成的JSON就是bmap.mapStyle.styleJson的值

百度地图个性化编辑器

4. 绘制地图
项目代码里面包括echarts地图常用的带有起点和终点信息的线路图、散点图、带有涟漪特效动画的散点图。
```
