<!-- App.vue(親コンポーネント)に対する子コンポーネント -->
<script setup lang="ts">

// プロパティの型定義
interface Props {
    label: string
}

const emit = defineEmits<{
    (e: 'click'): void // クリックイベント
}>()

// definePropsは、受け取るコンポーネントを定義する
// Props とは、親コンポーネントから子コンポーネントにデータを渡す仕組み
const props = defineProps<Props>()

function handleClick() {
    emit('click')
}

</script>

<template>
    <button @click="handleClick" class="counter-button">
        {{  props.label }}
    </button>
</template>

<style scoped>
.counter-button {
  font-size: 20px;
  padding: 10px 20px;
  margin: 0 10px;
  cursor: pointer;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 4px;
}

.counter-button:hover {
  background-color: #45a049;
}
</style>