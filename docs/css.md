# 报错 node-sass 不支持64位
- 安装node14版本  16版本太高了 node-sass不支持
# normalize.css npm包 可用于css reset

margin：auto为什么只能实现水平居中，不能实现垂直居中?
因为默认的宽度规则是“适应于父级”规则（在水平方向上自动扩充）。即

margin-left+border-left-width+padding-left+width+padding-right+border-right-width+margin-right= width of containing block

当一个绝对定位元素，其对立定位方向属性同时有具体定位数值的时候，流体特性就发生了。

具有流体特性绝对定位元素的margin:auto的填充规则和普通流体元素一模一样：

如果一侧定值，一侧auto，auto为剩余空间大小；

如果两侧均是auto, 则平分剩余空间

数组浅拷贝 arr.slice()
对象浅拷贝 Object.assign(targetObj,sourceObj)
