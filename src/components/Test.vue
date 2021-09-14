<script lang="ts">
import { ref } from "@vue/reactivity";
import {onBeforeMount, onMounted, watch } from "@vue/runtime-core";
import { defineComponent, reactive } from "vue";

export default defineComponent ({
  props: ["msg"],
  setup() {
    const hello = "hello world";
    const game = "游戏";

    // defineProps

    onBeforeMount(() => {
      console.log("onBeforeMount");
    });

    onMounted(() => {
      console.log("onMounted");
    });

    interface DataProperty {
      girls: string[];
      selectGirl: string;
      selectGirlFun: (index: number) => void;
    }

    const data: DataProperty = reactive({
      girls: ["大脚", "刘颖", "丽丽"],
      selectGirl: "",
      selectGirlFun: (index: number): void => {
        data.selectGirl = data.girls[index];
      },
    });

    watch(() => data.selectGirl, (value, oldValue) => {
        console.log(`${value} ${oldValue}`)
        document.title = value
    })

    return {
      hello,
      game,
      data,
    };
  },
});
</script>

<template>
  <div>{{ msg }} {{ hello }} {{ game }}</div>

  <h2 class="name">欢迎你</h2>
  <button
    v-for="(item, index) in data.girls"
    v-bind:key="index"
    @click="data.selectGirlFun(index)"
  >
    {{ item }}
  </button>
  <div>你选择了{{ data.selectGirl }}</div>
</template>