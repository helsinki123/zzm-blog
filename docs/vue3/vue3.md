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
# 在 Vite2 与 Vue3 中使用Mockjs
```
1. 安装mockjs

npm install mockjs --save-dev
2. 安装vite-plugin-mock

npm i vite-plugin-mock cross-env -D
3.在 package.json 中设置环境变量

复制代码
{
    "scripts": {
        // 修改dev构建脚本的命令
        "dev": "cross-env NODE_ENV=development vite",
        "build": "vite build",
        "serve": "vite preview"
    }
}
复制代码
4.在 vite.config.js 中添加 mockjs 插件

复制代码
import vue from "@vitejs/plugin-vue"
import { viteMockServe } from "vite-plugin-mock"
import { defineConfig } from "vite"

export default defineConfig({
    plugins: [
        vue(),
        viteMockServe({
            supportTs: true     //如果使用 js发开，则需要配置 supportTs 为 false
        })
    ]
})
复制代码
5.在项目中根目录创建 mock 文件夹，建立getUsers.ts在其中创建需要的数据接口

复制代码
// 仅做示例: 通过GET请求返回一个名字数组
export default [
    {
        url: "/api/getUsers",
        method: "get",
        response: () => {
            return {
                code: 0,
                message: "ok",
                data: ["tom", "jerry"],
            }
        }
    }
]
复制代码
 6. 修改App.vue，请求接口，显示数据

 

复制代码
<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <div v-for="(item,index) in users">
    {{index+1}}-{{item}}
  </div>
</template>

<script lang="ts">
import { defineComponent, onMounted, ref } from "vue";
import axios from "axios"

export default defineComponent({
  name: 'App',
  setup() {
    let users = ref([])

    onMounted(()=>{
      axios.get(`/api/getUsers`).then(res=>{
        users.value = res.data.data
        console.log('users', users)
      }).catch(err=>{
        console.log(err)
      })
    })

    return { users }
  }
})
</script>
```
# element-plus el-menu递归组件
## 父组件
```
<template>
  <div class="wrap">
    管理系统
    <el-menu>
      <template v-for="menu in menuData">
        <menuTree
          v-if="menu.children.length > 0"
          :key="menu.index"
          :menu="menu"
        ></menuTree>
      </template>
    </el-menu>
  </div>
</template>

<script>
import { reactive, toRefs, onBeforeMount, onMounted } from "vue";
import menuTree from "./childMenu.vue";
export default {
  props: {},
  name: "menufather",
  components: {
    menuTree,
  },
  setup() {
    const menuData = reactive([
      {
        index: "1",
        name: "首页",
        icon: "",
        children: [
          {
            index: "1-1",
            name: "表格",
            path: "",
            children: [
              {
                index: "1-6-1",
                name: "1-6-1",
                path: "",
                children: [],
              },
            ],
          },
          {
            index: "1-5",
            name: "1-5",
            path: "",
            children: [
              {
                index: "1-6-1",
                name: "1-6-1",
                path: "",
                children: [],
              },
            ],
          },
        ],
      },
      {
        index: "2",
        name: "父级",
        icon: "",
        children: [
          {
            index: "2-1",
            name: "2-1子级",
            path: "",
            children: [],
          },
        ],
      },
    ]);
    return { menuData };
  },
};
</script>
<style scoped>
.wrap {
  width: 200px;
  height: 100vh;
  background-color: aqua;
}
p {
  width: 200px;
  height: 200px;
  margin-top: 50px;
  background-color: aqua;
}
</style>

```
## 子组件
```
<template>
  <el-sub-menu v-if="menu.children.length > 0" :index="menu.index">
    <template #title>
      <el-icon><circle-plus /></el-icon>
      <span>{{ menu.name }}</span>
    </template>
    <template v-for="child in menu.children">
      <menu-tree
        v-if="child.children.length > 0"
        :menu="child"
        :key="child.index"
      ></menu-tree>
      <el-menu-item v-else :index="child.path" :key="child.index">{{
        child.name
      }}</el-menu-item>
    </template>
  </el-sub-menu>
</template>

<script>
import { onMounted } from "vue";
import { CirclePlus, Delete, Search } from "@element-plus/icons-vue";
export default {
  name: "menu-tree",
  props: {
    menu: {},
  },
  setup(props, ctx) {
    onMounted(() => {});
    console.log("menu", props.menu);
    return {};
  },
};
</script>

<style lang="scss"></style>

```
# 深入源码剖析Vue3 ref
[Vue3 ref](https://www.jianshu.com/p/a61c715c5cad)
# 组合式API图解
[掘金链接](https://juejin.cn/post/6890545920883032071)
# ref和reactive的区别

- ref 用来定义 基本类型
- ref 底层通过 Object.defineProperty()的 get 于 set 来实现响应式 (数据劫持)
- ref定义的数据：操作数据需要.value，读取数据时模板中直接读取不需要.value
1. reactive用来定义：对象或数组类型数据。
2. reactive通过使用Proxy来实现响应式（数据劫持）, 并通过Reflect操作源代码内部的数据。
3. reactive定义的数据：操作数据与读取数据：均不需要.value。
- ref可以定义对象或数组的，它只是内部自动调用了reactive来转换。

