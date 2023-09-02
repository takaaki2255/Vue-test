<script setup>
import AppHeader from "./components/AppHeader.vue";
import Todolist from "./components/Todolist.vue";
import { ref } from "vue";

const todos = ref([]);
const newTodo = ref("");

const addTodo = () => {
  todos.value.push(newTodo.value);
  newTodo.value = "";
};

const removeTodo = (index) => {
  todos.value.splice(index, 1);
};
</script>
<template>
  <AppHeader color="blue">My Todo</AppHeader>

  <input type="text" size="30" v-model="newTodo" />
  <button @click="addTodo()">追加</button>

  <Todolist :todos="todos" @removeTodo="removeTodo" />
</template>
