<template>
    <div>
        <h1>Vue3学習 - step3: v-if</h1>
        <button @click="toggleShow">表示切り替え</button>

        <p v-if="isVisible">この文章が表示されます</p>
        <p v-else>この文章はふざけています</p>
    </div>
</template>

<script setup lang="ts">
import { ref } from "vue"

const isVisible = ref<Boolean>(true)

const toggleShow = () => {
    isVisible.value = !isVisible.value
}

</script>