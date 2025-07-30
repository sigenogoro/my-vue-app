<template>
    <div>
        <h1>Vue3学習 - Step2 & 3 reactive, v-model</h1>
        <p>名前: {{ userObject.name }}</p>
        <p>年齢: {{ userObject.age }}</p>

        <!-- Step3: v-model -->
         <label>メッセージの入力: </label>
         <input v-model="message" type="text">
         <p>入力内容: {{ message }}</p>
    </div>
</template>

<script setup lang="ts">
import {ref, reactive} from 'vue'

const userObject = reactive({
    name: "Vue太郎",
    age: 25
})

const message = ref<string>("")


</script>