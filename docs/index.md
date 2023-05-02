
# lc-vue-text-tip

## 安装

```
npm i lc-vue-text-tip
```

## 基本使用

<script setup lang="ts">
  import { VueTextTip } from 'lc-vue-text-tip'
</script>

<div>
  <VueTextTip msg='阿斯顿发射点发射点发射点阿斯顿发射点发射点'/>  
</div>

<div style='width: 100px;'>
  <VueTextTip msg='阿斯顿发射点发射点发射点阿斯顿发射点发射点'/>  
</div>

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
