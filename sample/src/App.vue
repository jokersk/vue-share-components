<script setup>
import FadeEffect from "vue-share-components/components/FadeEffect.vue";
import Collapse from "vue-share-components/components/Collapse.vue";
</script>

<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Hello Vue 3 + Vite" />
  <Collapse>
    <template v-slot:trigger>
      <button>click me</button>
    </template>
    <template v-slot>
      <div>content</div>
    </template>
  </Collapse>
  <div style="height: 4000px"></div>
  <FadeEffect>
    <div>1212121</div>
  </FadeEffect>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
