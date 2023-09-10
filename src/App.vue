<!-- アプリ開発名　簡易型ジャンケンポン -->
<script setup>
import { ref } from "vue";

const title = "じゃんけん　　ポンッ！ 最初に表示　　ボタン後消す";
const message = "ボタンを押してね　最初に表示　　ボタン後消す";
const answer = "勝ち　負け　引き分け　ボタンを押したら表示";
// const handGu = ref([
//   {
//     name: "グー",
//     image: "./public/image/Gu.png",
//     click: false,
//   },
// ]);
// const handChoki = ref([
//   {
//     name: "チョキ",
//     image: "./public/image/choki.png",
//     click: false,
//   },
// ]);
// const handPa = ref([
//   {
//     id: 3,
//     name: "パー",
//     image: "./public/image/pa.png",
//     click: false,
//   },
// ]);
</script>

<template>
  <head>
    <meta charset="utf-8" />
    <title>rock paper scissors</title>
  </head>

  <body>
    <header>
      <h3>じゃんけんをしましょう</h3>
    </header>
    <div class="container">
      <h1 v-html="title"></h1>
      <p v-html="message"></p>
      <div class="table">
        <button class="btn">グー</button>
        <button class="btn">チョキ</button>
        <button class="btn">パー</button>
      </div>
      <p v-html="answer"></p>
    </div>
    <footer>
      <h2>勝てたら良い事があるかもね‼︎</h2>
    </footer>
  </body>
</template>
