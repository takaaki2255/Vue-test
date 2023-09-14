<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  setup() {
    //　勝敗の結果を表す変数を定義。初期値は空文字
    const result = ref("");
    //　コンピュータの手を表す変数を定義
    const computer = ref("");
    // コンピュータの手を画像で表示
    // const image
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
    }
    return {
      result,
      computer,
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
  <div>
    <header>
      <h2>じゃんけんをしましょう</h2>
    </header>
    <h1>じゃんけんゲーム</h1>
    <h2 v-if="result == ''">ボタンを押してね</h2>
    <h1 class="text">相手： {{ computer }}</h1>
    <div class="table">
      <button class="btn" @click="play('グー')">グー</button>
      <button class="btn" @click="play('チョキ')">チョキ</button>
      <button class="btn" @click="play('パー')">パー</button>
    </div>
    <h1 class="text">{{ result }}</h1>
  </div>
  <footer>
    <h2>勝てたら良い事があるかもね‼︎</h2>
  </footer>
</template>
