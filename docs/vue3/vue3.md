# 在vite.config.js里面添加跨域配置
```
server: {
      open: true,//启动项目自动弹出浏览器
      port: 3000,//启动端口
      proxy: {
        '/api': 'https://api.it120.cc/'//代理网址
      }
    }
```
- 使用get("/api/shop/goods/category/all") 便可跨域

# vue3全局挂载
main.js
```
import App from './App.vue'
const app = createApp(App)
app.config.globalProperties.$http = http
```
使用
```
const instance = getCurrentInstance();
instance.appContext.config.globalProperties.$http
```
# vue3支持多个根标签

# 可以在reactive({})里面定义所有响应式数据

# vue3父子组件通信写法
父组件
- <copy foo="1" @change="testHttp"></copy>
子组件
```
<script setup>// 有setup 不需要引入defineProps和defineEmits
const props = defineProps({
  foo: String
})

const emit = defineEmits(['change'])
function testHttp() {
  emit("change")
}
</script>
```
# vue3 生命周期
引入onMounted便可使用
```
onMounted(()=>{
  console.log("onMounted");
})
```

# 获取当前路由实例
```
vue以前获取参数用this.$route获取
import {useRouter } from 'vue-router'
vue3通过router.currentRoute.value.path
这是currentRoute里面的值
![currentRoute](https://upload-images.jianshu.io/upload_images/14976544-241eb3776f23eb36.png?imageMogr2/auto-orient/strip|imageView2/2/w/809/format/webp)
```

# watch
```
watch(DATA.name, (newValue, oldValue) => {
document.title = newValue;
});
```

# ref获取DOM
```
<div class="helloworld" ref="aaa">aaaaaaa</div>
const aaa = ref(null)//要在onMounted外面
onMounted(()=>{
console.log(aaa.value);
})
```
