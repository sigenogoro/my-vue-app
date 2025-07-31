<template>
  <div>
    <h1>Vue3学習 - Step1</h1>
    <p>カウント: {{ count }}</p>
    <button @click="increment">+1</button>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

// refで数値を管理
const count = ref<number>(0)

// 関数定義
const increment = () => {
  count.value++ // refは.valueでアクセス
}
</script>