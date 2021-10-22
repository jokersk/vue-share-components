<script setup>
import FadeEffect from "vue-share-components/components/FadeEffect.vue";
import Collapse from "../../components/Collapse.vue";
</script>

<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Hello Vue 3 + Vite" />
  <Collapse>
    <template v-slot:trigger>
      <button>click me</button>
    </template>
    <template v-slot>
      <div style="max-width: 300px; margin: auto">
        Sociis natoque penatibus et magnis dis parturient montes, nascetur
        ridiculus mus. Nunc faucibus posuere turpis. Sed laoreet, est sed
        gravida tempor, nibh enim fringilla quam, et dapibus mi enim sit amet
        risus. Nulla sollicitudin eros sit amet diam. Aliquam ante. Vestibulum
        ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia
        Curae; Ut et est. Donec semper nulla in ipsum. Integer elit. In pharetra
        lorem vel ante. Sed sed justo. Curabitur consectetuer arcu. Etiam
        placerat est eget odio. Nulla facilisi. Nulla facilisi. Mauris non
        neque. Suspendisse et diam. Sed vestibulum malesuada ipsum. Cras id
        magna. Nunc pharetra velit vitae eros. Vivamus.
      </div>
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
