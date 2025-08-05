<!-- 今回学ぶこと
emit: 子→親（イベントを通知する）← 今回

身近な例
- 子供が親に「お腹すいた！」と伝える
- ボタンが「クリックされた！」とアプリに伝える
-->

<template>
    <div style="border: 1px solid #ccc; padding: 20px; margin: 10px;">
        <h3>👤 {{ name }}</h3>
        <p>年齢: {{ age }}歳</p>
        
        <!-- 子から親に「削除して！」と伝えるボタン -->
        <button @click="handleDelete" style="background: red; color: white; padding: 5px;">
            🗑️ 削除
        </button>
        
        <!-- 子から親に「年齢を増やして！」と伝えるボタン -->
        <button @click="handleAgeUp" style="background: blue; color: white; padding: 5px;">
            🎂 誕生日
        </button>
    </div>
</template>

<script setup lang="ts">

interface Props {
    name: string,
    age: number
}

interface Emits {
    delete: [],
    ageUpdate: [newAge: number]
}

const props = defineProps<Props>()
const emit = defineEmits<Emits>()

const handleDelete = () => {
    emit("delete")
}

const handleAgeUp = () => {
    const newAge = props.age + 1
    emit("ageUpdate", newAge)
}


</script>
