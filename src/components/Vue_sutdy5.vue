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

アプリ開発名　簡易型ジャンケンポン
<script setup>
import { ref } from "vue";
import { createApp } from "vue";

const title = "じゃんけん ポンッ！ 最初に表示 ボタン後消す";
const message = "ボタンを押してね 最初に表示 ボタン後消す";
const answer = "dld";
const pushoff = ref(0);
const add = () => {
  pushoff.value = "itemes.id";
};

// const items = ref([
//   {
//     id: 1,
//     name: "グー",
//     image: "./public/image/Gu.png",
//   },
//   {
//     id: 2,
//     name: "チョキ",
//     image: "./public/image/choki.png",
//   },
//   {
//     id: 3,
//     name: "パー",
//     image: "./public/image/pa.png",
//   },
// ]);

createApp({
  data() {
    return {
      hand: ["goo", "choki", "paa"],
      enemyHand: "",
      enemyHandImage: "",
      answer: "",
    };
  },
  methods: {
    selectHand: function (myHand) {
      // 敵の手をランダムに決める
      var index = Math.floor(Math.random() * Math.floor(3));
      this.enemyHand = this.hand[index];
      if (this.enemyHand === "goo") {
        this.enemyHandImage = "";
      } else if (this.enemyHand === "choki") {
        this.enemyHandImage = "";
      } else if (this.enemyHand === "paa") {
        this.enemyHandImage = "";
      }

      // 勝敗判定
      if (myHand === this.enemyHand) {
        return (this.answer = "引き分け!");
      }

      if (myHand === "goo") {
        if (this.enemyHand === "choki") {
          return (this.answer = "勝ち!");
        }
        if (this.enemyHand === "paa") {
          return (this.answer = "負け");
        }
      }

      if (myHand === "choki") {
        if (this.enemyHand === "paa") {
          return (this.answer = "勝ち!");
        }
        if (this.enemyHand === "goo") {
          return (this.answer = "負け");
        }
      }

      if (myHand === "paa") {
        if (this.enemyHand === "goo") {
          return (answer = "勝ち!");
        }
        if (this.enemyHand === "choki") {
          return (answer = "負け");
        }
      }
    },
  },
}).mount("#app");
</script>

<template>
  <head>
    <meta charset="utf-8" />
    <title>rock paper scissors</title>
  </head>

  <body>
    <header>
      <h2>じゃんけんをしましょう</h2>
    </header>
    <div id="app">
      <h1 v-if="pushoff == 0">
        {{ title }}<br />
        {{ message }}
      </h1>
      <div class="table">
        <button class="btn" @click="selectHand('goo')">グー</button>
        <button class="btn" @click="selectHand('choki')">チョキ</button>
        <button class="btn" @click="selectHand('paa')">パー</button>
        <!-- <button
          class="btn"
          v-for="item in items"
          :key="item.id"
          @click="'add', 'item.name'"
        >
          {{ item.name }}
        </button> -->
      </div>
      <h1>{{ answer }}</h1>
    </div>
    <footer>
      <h2>勝てたら良い事があるかもね‼︎</h2>
    </footer>
  </body>
</template>
