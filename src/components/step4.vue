<template>
    <div>
        <h1>Vue3学習 - step4: v-for</h1>
        <h3>趣味リスト</h3>
        <ul>
            <li v-for="(hobby, index) in hobbies" :key="index">
                {{ index + 1 }}. {{ hobby }}
            </li>
        </ul>

        <button @click="addHobby">趣味を追加</button>
    </div>
</template>

<script setup lang="ts">
import { ref } from "vue"

const hobbies = ref<string[]>(["プログラミング", "読書", "映画鑑賞"])

const addHobby = () => {
    const newHobbies = ["料理", "旅行", "ゲーム", "運動", "音楽鑑賞"]
    const randomHobby = newHobbies[Math.floor(Math.random() * newHobbies.length)]

    if(!hobbies.value.includes(randomHobby)) {
        hobbies.value.push(randomHobby)
    }
}

</script>