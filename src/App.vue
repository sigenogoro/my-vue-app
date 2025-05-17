<!-- 
Vue3 + Viteの基本構成, componentAPIを使用
setup関数を宣言することで、componentAPIのより簡単に宣言することができる
Vue3のコンポーネントは、Vue2のオプションAPIに代わって、setup関数を使用して作成されます。
lang="ts"にすることで TypeScirptの利用することができます
「単一ファイルコンポーネント」（SFC）の基本構造です。1つのファイルに、HTMLテンプレート、JavaScriptロジック、CSSスタイルを記述できます。
-->
<script setup lang="ts">
import { ref } from 'vue'
</script>

<template>
  <div class="counter-app">
    <h1>シンプルカウント</h1>
    
  </div>
</template>
