<!-- 
Vue3 + Viteの基本構成, componentAPIを使用
setup関数を宣言することで、componentAPIのより簡単に宣言することができる
Vue3のコンポーネントは、Vue2のオプションAPIに代わって、setup関数を使用して作成されます。
lang="ts"にすることで TypeScirptの利用することができます
「単一ファイルコンポーネント」（SFC）の基本構造です。1つのファイルに、HTMLテンプレート、JavaScriptロジック、CSSスタイルを記述できます。
-->
<script setup lang="ts">
import { ref } from 'vue'

const count = ref(0) 

// カウントを増やす関数
function increment() {
  count.value++
}

function decrement() {
  count.value--
}
</script>

<template>
  <div class="counter-app">
    <h1>シンプルカウント</h1>
    <div class="counter">
      <button @click="decrement">減少</button>
      <span>{{ count }}</span>
      <button @click="increment">追加</button>
    </div>

    <p>現在のカウント: {{ count }}</p>
  </div>
</template>

<!-- scopedはCSSをこのコンポーネントにだけ抑えること -->
<style scoped>
.counter-app {
  font-family: Arial, sans-serif;
  max-width: 400px;
  margin: 0 auto;
  text-align: center;
  padding: 20px;
}

.counter {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 20px 0;
}

button {
  font-size: 20px;
  padding: 10px 20px;
  margin: 0 10px;
  cursor: pointer;
}

span {
  font-size: 24px;
  padding: 0 20px;
}

</style>