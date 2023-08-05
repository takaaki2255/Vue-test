<!-- 
  1回目の編集
  <script setup>
import { ref, computed } from "vue";

import WelcomeItemVue from "./components/WelcomeItem.vue";

const message = computed(() => {
  return "ようこそ " + myname.value + "さん";
});
const color = "white";
const myname = ref("");
</script> -->

<!-- <template>
  <h1>Vue 3</h1>
  <p>23 + 34 = {{ answer }}</p>
  <p>お名前は? : <input type="text" size="30" v-model="myname" /></p>
  <p v-html="message" :style="{ color: color, 'background-color': 'blue' }"></p>
</template> -->

<!-- 
  2回目の編集
<script setup>
import { ref } from "vue";
const number = ref(0);
const add = () => {
  number.value++;
};
</script>

<template>
  <input type="text" size="30" v-model="number" />
  <button @click="add()">+1</button>
</template> -->

<script setup>
import { ref } from "vue";

const todos = ref([]);
const newTodo = ref("");

const addTodo = () => {
  todos.value.push(newTodo.value);
  newTodo.value = "";
};
</script>

<template>
  <input type="text" size="30" v-model="newTodo" />
  <button @click="addTodo()">追加</button>

  <ul>
    <li v-for="(todo, i) in todos" v-bind:key="i">{{ todo }}</li>
  </ul>
</template>
