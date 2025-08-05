<template>
    <div>
        <h2>computed 型付け（10分学習）</h2>
        <div style="border: 1px solid blue; padding: 10px; margin: 5px;">
            <h3>1. 自動型推論</h3>
            <p>数値: {{ count }} → 2倍: {{ doubleCount }}</p>
            <button @click="count++">+1</button>
        </div>
        <!-- 明示的型指定 -->
        <div style="border: 1px solid green; padding: 10px; margin: 5px;">
            <h3>2. 明示的型指定</h3>
            <p>{{ message }}</p>
        </div>

        <!-- 実用例 -->
        <div style="border: 1px solid red; padding: 10px; margin: 5px;">
            <h3>3. 実用例</h3>
            <p>商品数: {{ products.length }}</p>
            <p>合計: {{ totalPrice }}円</p>
        </div>
    </div>
</template>

<script setup lang="ts">
import { reactive, computed } from 'vue'

// 1, 自動型推論
const count = 0
const doubleCount = computed(() => count * 2)

const message = computed<string>(() => {
    return `現在のカウント: ${count}`
})

interface Products {
    name: string,
    price: number
}

const products = reactive<Products[]>([
    { name: 'Vue本', price: 3000 },
    { name: 'TS本', price: 3500 }
])

const totalPrice = computed(() => {
    return products.reduce((sum, p) => sum + p.price, 0)
})

</script>