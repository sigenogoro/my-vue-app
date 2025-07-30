<template>
    <div>
        <h1>Vue3学習 - Step2</h1>
        <p>名前: {{ userObject.name }}</p>
        <p>年齢: {{ userObject.age }}</p>
    </div>
</template>

<script setup lang="ts">
import {reactive} from 'vue'

const userObject = reactive({
    name: "Vue太郎",
    age: 25
})


</script>