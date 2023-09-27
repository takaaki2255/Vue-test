<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  setup() {
    //　勝敗の結果を表す変数を定義。初期値は空文字
    const result = ref("");
    //　コンピュータの手を表す変数を定義
    const computer = ref("");
    // コンピュータの手を画像で表示
    const imgs = ref("");
    // コンピュータの手をランダムに決める
    function play(player: string) {
      const hands = ["グー", "チョキ", "パー"];
      computer.value = hands[Math.floor(Math.random() * hands.length)];
      // じゃんけんの勝敗を判定するロジック
      if (player === computer.value) {
        result.value = "引き分け";
      } else if (
        (player === "グー" && computer.value === "チョキ") ||
        (player === "チョキ" && computer.value === "パー") ||
        (player === "パー" && computer.value === "グー")
      ) {
        result.value = "勝ち";
      } else {
        result.value = "負け";
      }
      // 画像の表示を変更する
      // if (computer.value === "グー") {
      //   imgs.value = require("../assets/images/Gu.png").default;
      // } else if (computer.value === "チョキ") {
      //   imgs.value = require("../assets/images/choki.png").default;
      // } else if (computer.value === "パー") {
      //   imgs.value = require("../assets/images/Pa.png").default;
      // } else {
      //   imgs.value = require("../assets/images/top.png").default;
      // }
    }
    return {
      result,
      computer,
      imgs,
      play,
    };
    //   画像を表示させる
    // if(computer.value === "グー") {
    //   Image.value =;
    // } elseif (  computer.value === "チョキ") {
    //   Image.value =;
    // } else {
    //   Image.value =;
    // }
  },
});
</script>

<template>
  <div id="app">
    <header>
      <h2>じゃんけんをしましょう</h2>
    </header>
    <p>じゃんけん</p>
    <img :src="imgs" alt="Logo" class="header__logo" />
    <p v-if="result == ''">ボタンを押してね</p>
    <p class="text">{{ computer }}</p>
    <div class="table">
      <button class="btn" @click="play('グー')">グー</button>
      <button class="btn" @click="play('チョキ')">チョキ</button>
      <button class="btn" @click="play('パー')">パー</button>
    </div>
    <p class="text">{{ result }}</p>
  </div>
  <footer>
    <p>勝てたら良い事があるかもね‼︎</p>
  </footer>
</template>
