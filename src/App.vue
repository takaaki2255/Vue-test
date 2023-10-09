<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  setup() {
    //　勝敗の結果を表す変数を定義。初期値は空文字
    const result = ref("");
    //　コンピュータの手を表す変数を定義
    const computer = ref("");
    // コンピュータの手を画像で表示
    const imgs = ref("top");
    // コンピュータの手をランダムに決める
    function play(player: string) {
      const hands = ["グー", "チョキ", "パー"];
      computer.value = hands[Math.floor(Math.random() * hands.length)];
      // 画像の表示を変更する
      if (computer.value === "グー") {
        imgs.value = "Gu";
      } else if (computer.value === "チョキ") {
        imgs.value = "choki";
      } else {
        imgs.value = "Pa";
      }
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
      imgs,
      play,
    };
  },
});
</script>

<template>
  <div id="app">
    <header>
      <h1>じゃんけんアプリ</h1>
    </header>
    <p>ジャンケンッ‼︎</p>
    <img
      :src="`./src/assets/images/${imgs}.png`"
      alt="相手の手"
      class="header__logo"
    />
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
    <p class="under">プロトタイプ</p>
  </footer>
</template>
