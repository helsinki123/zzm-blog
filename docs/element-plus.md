# :width
```
 <el-aside
      :width="isCollapse ? '60px' : '200px'"
      :class="isCollapse ? 'hide-aside' : 'show-side'"
      v-show="!contentFullScreen"
    >
    :width妙啊
```

# 全局引入icon
## JS
```
import * as Icons from "@element-plus/icons-vue";

// 注册全局组件
Object.keys(Icons).forEach((key) => {
  app.component(key, Icons[key]);
});

```
## TS
```
import * as Icons from "@element-plus/icons-vue";

// 注册全局组件
Object.keys(Icons).forEach((key) => {
  app.component(key, Icons[key as keyof typeof Icons]);
});
```
## CusIcon.vue
```
<template>
  <el-icon :size="size" :color="color">
    <component class="el-icon" :is="icon" />
  </el-icon>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
export default defineComponent({
  props: {
    icon: {
      type: String,
      default: "tools",
    },
    size: {
      type: Number,
      default: 14,
    },
    color: {
      type: String,
      default: "#000000",
    },
  },
  setup(props) {
    let icon = ref(props.icon);
    // 不选择图标的时候，后端会默认传#，如果不做处理会报错
    if (icon.value === "#") {
      icon.value = "tools";
    }
    return {
      icon,
    };
  },
});
</script>
```
## 使用
```
import CusIcon from "@/components/CusIcon.vue";
<el-icon><add-location /></el-icon>
```
