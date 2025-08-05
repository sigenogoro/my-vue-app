<template>
    <div>
        <h1>Vue3学習 - Step7: emit</h1>
        <p>子コンポーネントからのイベントを受け取るデモ</p>
        
        <!-- 各ユーザーカードに削除とageUpイベントリスナーを設定 -->
        <Step7Child 
            v-for="(user, index) in users" 
            :key="index"
            :name="user.name" 
            :age="user.age"
            @delete="deleteUser(index)"
            @age-update="updateUserAge(index, $event)"
        />

        <!-- $event: 子から送られてきたデータを表す変数、一つしか受け取ることができない -->
        
        <hr>
        <button @click="addUser" style="background: green; color: white; padding: 10px;">
            ➕ ユーザー追加
        </button>
    </div>
</template>


<script setup lang="ts">
import { reactive } from 'vue'
import Step7Child from './step7-child.vue'

interface User {
    name: string
    age: number
}

// ユーザーリストを管理
const users = reactive<User[]>([
    { name: 'Vue太郎', age: 25 },
    { name: 'Vue花子', age: 23 },
    { name: 'TypeScript次郎', age: 30 }
])

const deleteUser = (index: number) => {
    console.log(`${index}番目のユーザーを削除します`)
    users.splice(index, 1)
}

const updateUserAge = (index: number, newAge: number) => {
    console.log(`${index}番目のユーザーの年齢を${newAge}歳にします`)
    users[index].age = newAge
}


const addUser = () => {
    const newUser: User = {
        name: `新ユーザー${users.length + 1}`,
        age: Math.floor(Math.random() * 50) + 20
    }
    users.push(newUser)
}
</script>