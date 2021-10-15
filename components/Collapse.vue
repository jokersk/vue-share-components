<template>
  <div>
    <div @click="toggle">
      <slot name="trigger" :is-open="isOpen"></slot>
    </div>
    <div ref="content" class="overflow-hidden transition-all duration-300">
      <slot :open="open"></slot>
    </div>
  </div>
</template>
<script setup>
import { ref, onMounted, provide } from "vue";
const content = ref(null);
const isOpen = ref(false);
let height = 0;
let el;
const toggle = () => {
  if (!isOpen.value) {
    return open();
  }
  close();
};

const close = () => {
  setHeight(0);
  isOpen.value = false;
};
const open = () => {
  setHeight(height);
  isOpen.value = true;
};
const setHeight = (value) => {
  el.style.height = value + "px";
};
onMounted(() => {
  el = content.value;
  height = el.getBoundingClientRect().height;
  setHeight(height);
  if (!isOpen.value) {
    setHeight(0);
  }
});
</script>

