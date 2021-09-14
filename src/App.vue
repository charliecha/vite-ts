<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import { reactive, ref, toRef, toRefs } from "@vue/reactivity";
import Test from "./components/Test.vue";
import HelloWorld from "./components/HelloWorld.vue"

import "./assets/app.css";
import test from "./assets/test.json";
import { onMounted } from "@vue/runtime-core";
import { onRenderTracked, onRenderTriggered } from "vue";

onMounted(() => {
  console.log(test);
});

onRenderTracked(event => {
  console.log(`onRenderTracked `)
  console.log(event)
})

onRenderTriggered(event => {
  console.log(`onRenderTriggered`)
  console.log(event)
})



// const refData = toRefs(data)

// const girls = ref(["大脚", "刘颖", "丽丽"]);
// const selectGirl = ref("");
// const selectGirlFun = (index: number) => {
//   selectGirl.value = girls.value[index];
// };
const hello = "hello"
</script>

<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Hello Vue 333 + TypeScript + Vite" />
  <Test :msg="hello"></Test>
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

.name {
  color: green;
}
</style>
