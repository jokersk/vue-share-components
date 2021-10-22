<template>
  <div>
    <div @click="toggle">
      <slot name="trigger" :is-open="isOpen"></slot>
    </div>
    <div ref="content">
      <slot :open="open"></slot>
    </div>
  </div>
</template>
<script setup>
import { ref, onMounted } from "vue";
const content = ref(null);
const isOpen = ref(false);
let height = null;
let el;
const toggle = () => {
  if (!isOpen.value) {
    return open();
  }
  close();
};

const transitionStyles = {
  overflow: "hidden",
  transitionProperty: "height",
  transitionDuration: `0.4s`,
  transitionTimingFunction: "cubic-bezier(0.4, 0.0, 0.2, 1)",
};
const setStyle = (el, styles) => {
  Object.keys(styles).forEach((key) => {
    el.style[key] = styles[key];
  });
};
const close = () => {
  setHeight(0);
  isOpen.value = false;
};
const onceSetStyle = once(setStyle);
const getHeight = () => {
  if (!height) {
    el.style.height = "auto";
    height = el.getBoundingClientRect().height;
    el.style.height = 0;
  }
  return height;
};
const open = () => {
  const full = getHeight();
  onceSetStyle(el, transitionStyles);
  setTimeout(() => {
    setHeight(full);
  });
  isOpen.value = true;
};
onMounted(() => {
  el = content.value;
  el.style.overflow = "hidden";
  if (!isOpen.value) {
    setHeight(0);
  }
});

function setHeight(value) {
  el.style.height = value + "px";
}
function once(fn) {
  let called = false;
  return function (...arg) {
    if (!called) {
      fn(...arg);
      called = true;
    }
  };
}
</script>

