<script setup>
import { ref, computed } from "vue";

import WelcomeItemVue from "./components/WelcomeItem.vue";

const message = computed(() => {
  return "ようこそ " + myname.value + "さん";
});
const color = "white";
const myname = ref("");
</script>
-->

<template>
  <h1>Vue 3</h1>
  <p>23 + 34 = {{ answer }}</p>
  <p>お名前は? : <input type="text" size="30" v-model="myname" /></p>
  <p v-html="message" :style="{ color: color, 'background-color': 'blue' }"></p>
</template>
