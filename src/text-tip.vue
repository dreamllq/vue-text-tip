<template>
  <div ref='fBody' style='width:100%'>
    <div v-if='!isOver' ref='tipBody' style='width:100%;display: inline-block;'>
      <div
        ref='testSpan'
        class='test-span'>
        {{ props.msg }}
      </div>
    </div>
    <el-tooltip
      v-else
      class='box-item'
      effect='light'
      placement='right'
      :popper-class='props.popperClass'
    >
      <template #content>
        <div style='max-width: 200px'>
          {{ props.msg }}
        </div>
      </template>
      <div class='tip-box'>
        {{ props.msg }}
      </div>
    </el-tooltip>
  </div>
</template>

<script setup lang="ts">
import { ref, watch, nextTick } from 'vue';
import { useElementSize } from '@vueuse/core';
import { get } from 'lodash';
const props = defineProps({
  msg: {
    type: String,
    default: ''
  },
  popperClass: {
    type: String,
    default: undefined
  }
});
const testSpan = ref();
const tipBody = ref();
const isOver = ref(false);
const fBody = ref();
const { width } = useElementSize(fBody);

async function computedStyle() {
  isOver.value = false;
  await nextTick();
  let spanWidth = get(testSpan.value, 'offsetWidth', 0);
  if (spanWidth > tipBody.value.clientWidth) {
    isOver.value = true;
    return;
  }
  isOver.value = false;
}
watch(width, () => {
  computedStyle();
});

</script>
<style scoped>
.tip-box{
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
  width:100%;
  display: block;
}
.test-span{
  display: inline-block;
  white-space: nowrap;
}
</style>