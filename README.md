# lc-vue-text-tip

## 安装

```
npm i lc-vue-text-tip
```

## 依赖

- vue@3.x
- element-plus@2.x
- @vueuse/core
- lodash

## Demo

[demo](https://unpkg.com/lc-vue-text-tip/docs/.vitepress/dist/index.html) 

## 基本使用

```vue
<script setup lang="ts">
  import { VueTextTip } from 'lc-vue-text-tip'
</script>

<template>
  <div>
    <VueTextTip msg='阿斯顿发射点发射点发射点阿斯顿发射点发射点'/>  
  </div>

  <div style='width: 100px;'>
    <VueTextTip msg='阿斯顿发射点发射点发射点阿斯顿发射点发射点'/>  
  </div>
</template>
```

## Api

### Attributes

| 属性名 | 说明 | 类型 | 默认值 |
| ---- | ---- | ---- | ---- |
| msg | 文字 | string | '' |
| popperClass | popper class | string | - |
