<!-- 
Vue3 + Viteの基本構成, componentAPIを使用
setup関数を宣言することで、componentAPIのより簡単に宣言することができる
Vue3のコンポーネントは、Vue2のオプションAPIに代わって、setup関数を使用して作成されます。
lang="ts"にすることで TypeScirptの利用することができます
「単一ファイルコンポーネント」（SFC）の基本構造です。1つのファイルに、HTMLテンプレート、JavaScriptロジック、CSSスタイルを記述できます。
-->
<script setup lang="ts">
import { computed, ref } from 'vue'
import CounterButton from './components/CounterButton.vue'
import PropsSample from './components/PropsSample.vue'
import HelloButton from './components/HelloButton.vue'

const count = ref(0)
const message = ref('')

const countStatus = computed(() => {
  if(count.value > 0) return '正の値ですね〜'
  if(count.value < 0) return '負の値ですね〜'
  return 'ゼロなんですよね〜'
})

// カウントを増やす関数
function increment() {
  count.value++
}

function decrement() {
  count.value--
}

function handleSubmit() {
  console.log('② 親: submit を受け取った！')
  alert("子コンポーネントから submitイベントを受け取りました")
}

function reset() {
  count.value = 0
  message.value = 'カウントをリセット致します'

  setTimeout(() => {
    message.value = ''
  }, 3000)
}
</script>

<template>
  <PropsSample name="もげもげ" />
  <div class="counter-app">
    <h1>シンプルカウント</h1>
    <div v-if="message" class="message">
      {{ message }}
    </div>
    <div class="counter">
      <CounterButton label="-" @click="decrement" />
      <span>{{ count }}</span>
      <CounterButton label="+" @click="increment" />
    </div>

    <p>現在のカウント: {{ count }} ({{ countStatus }})</p>
    <button @click="reset" class="reset-button">リセット</button>
  </div>
  <div>
    <h1><HelloButton @click="handleSubmit" /></h1>
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

span {
  font-size: 24px;
  padding: 0 20px;
}

.message {
  background-color: #4CAF50;
  color: white;
  padding: 10px;
  margin: 10px 0;
  border-radius: 4px;
}

.reset-button {
  background-color: #f44336;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 4px;
  cursor: pointer;
  margin-top: 20px;
}

.reset-button:hover {
  background-color: #d32f2f;
}
</style>