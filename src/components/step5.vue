<template>
    <div>
        <h1>Vue3 - Step5: computed</h1>

        <p>数値: {{ count }}</p>
        <p>2倍の値: {{ doubleCount }}</p>
        <p>3倍の値: {{ tripleCount }}</p>
        
        <button @click="increment">+1</button>
        <button @click="decrement">-1</button>
        <button @click="reset">リセット</button>
    </div>
</template>

<script setup lang="ts">
import { ref, computed } from "vue"

const count = ref<number>(0)

const doubleCount = computed(() => count.value * 2)
const tripleCount = computed(() => count.value * 3)

const increment = () => {
    count.value++
}

const decrement = () => {
    count.value--
}

const reset = () => {
    count.value = 0
}

</script>