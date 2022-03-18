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
