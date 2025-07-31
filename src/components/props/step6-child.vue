<template>
    <div style="border: 2px solid green; padding: 20px; margin: 10px;">
        <h3>📦 荷物受取所（子コンポーネント）</h3>
        <div style="background: skyblue; padding: 15px; margin: 10px;">
            <h4>🎁 受け取った荷物の中身</h4>
            <p><strong>商品名:</strong>{{ productName }}</p>
            <p><strong>価格:</strong> {{ price }}円</p>
            <p><strong>カテゴリ:</strong> {{ category }}</p>
        </div>

        <button @click="checkProduct" style="background: orange; padding: 10px;">
            🔍 商品詳細を調べる
        </button>

        <div v-if="inspection" style="background: #e8f4f8; padding: 10px; margin-top: 10px;">
            <h4>📋 調査結果</h4>
            <p>{{ inspection }}</p>
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref } from "vue"

interface ProductProps {
    productName: string,
    price: number,
    category: string
}
const props = defineProps<ProductProps>()
const inspection = ref<string>("")

const checkProduct = () => {
    const report = `
        商品分析完了！
        名前: ${props.productName}
        価格帯: ${props.price >= 1000 ? '高価格帯' : '低価格帯'}
        カテゴリ: ${props.category}
        コスパ: ${props.price < 500 ? '良い' : 'まあまあ'}
    `

    inspection.value = report

    console.log('📊 商品分析:', props.productName, props.price, props.category)
}


</script>