<!-- 
emit/defineEmitsは、子コンポーネントから親コンポーネントにイベントを通知するための関数
【意味】
子コンポーネントから、「今こんなことが起きました！」と親に伝える仕組みです
-->

<script setup lang="ts">
const emit = defineEmits(['click'])
function handleClick() {
    console.log('① 子: handleClick 実行')
    emit('click') // 親に「submit」イベントを通知
}
</script>

<template>
  <button @click="handleClick">送信</button>
</template>