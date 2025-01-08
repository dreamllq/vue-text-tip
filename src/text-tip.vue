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
      :placement='placement'
      :enterable='props.enterable'
      :popper-class='props.popperClass'
    >
      <template #content>
        <div style='max-width: 200px'>
          {{ props.msg }}
        </div>
      </template>
      <div class='tip-box' :style='tipBoxStyle'>
        {{ props.msg }}
      </div>
    </el-tooltip>
  </div>
</template>

<script setup lang="ts">
import { ref, watch, nextTick, PropType, computed } from 'vue';
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
  },
  placement: {
    type: String as PropType<'top'|'top-start'|'top-end'|'bottom'|'bottom-start'|'bottom-end'|'left'|'left-start'|'left-end'|'right'|'right-start'|'right-end'>,
    default: 'right'
  },
  linClamp: {
    type: Number,
    default: 1
  },
  enterable: {
    type: Boolean,
    default: true
  }
});
const testSpan = ref();
const tipBody = ref();
const isOver = ref(false);
const fBody = ref();
const { width } = useElementSize(fBody);
const tipBoxStyle = computed(() => ({ '-webkit-line-clamp': props.linClamp }));

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
  text-overflow: ellipsis;
  overflow: hidden;
  width:100%;
  display: -webkit-box;
  -webkit-box-orient: vertical;
}
.test-span{
  display: inline-block;
  white-space: nowrap;
}
</style>