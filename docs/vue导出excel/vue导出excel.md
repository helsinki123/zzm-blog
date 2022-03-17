# vue3
```
 npm  install  -S file-saver
 npm  install  -S  xlsx
 npm  install  -D script-loader
```
将此文件复制到项目
[Export2Excel.js](https://github.com/helsinki123/zzm-blog/blob/main/docs/Export2Excel.js)
```
html
<button @click="handleExportExcel">导出</button>

js
const handleExportExcel = () => {
  const header = ["id", "name", "age", "address"];
  const data = [
    ["1", "zzm", "25", "addresstest"],
    ["1", "zzm", "25", "addresstest"],
    ["1", "zzm", "25", "addresstest"],
    ["1", "zzm", "25", "addresstest"],
  ];
  const fileName = "zzm";
  import("xxx/xxx/Export2Excel").then(({ arrayToExcel }) => {
    arrayToExcel({ header, data, fileName });
  });
};
```
![最终结果]()
# vue2
[此教程可行](https://www.cnblogs.com/chr506029589/p/13963768.html)
```
cnpm i vue-json-excel -S
import JsonExcel from 'vue-json-excel'
Vue.component('downloadExcel', JsonExcel)//必须在main.js全局注册才生效
```
