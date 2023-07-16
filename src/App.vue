<script setup>
// import { computed } from "vue";

import WelcomeItemVue from "./components/WelcomeItem.vue";

// const answer = computed(() => {
//   return 23 + 34;
// });

const message = "ようこそ　<strong>ともすた</strong>さん";
const color = "white";
</script>

<template>
  <h1>Vue 3</h1>
  <!-- <p>23 + 34 = {{ answer }}</p> -->
  <p v-html="message" :style="{ color: color, 'background-color': 'blue' }"></p>
</template>
