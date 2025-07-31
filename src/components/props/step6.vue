<template>
    <div>
        <h2>🏪 オンラインショップ</h2>
        <p>各商品カードに異なる商品情報を送っています</p>
        
        <!-- 同じ商品カードコンポーネントに異なる商品を表示 -->
        <VisualPropsDemo 
            productName="Vue.js入門書" 
            :price="2800" 
            category="プログラミング書籍"
        />
        
        <VisualPropsDemo 
            productName="TypeScript完全ガイド" 
            :price="3200" 
            category="技術書"
        />
        
        <VisualPropsDemo 
            productName="ワイヤレスマウス" 
            :price="1500" 
            category="PC周辺機器"
        />
    </div>
</template>

<script setup lang="ts">
import VisualPropsDemo from './step6-child.vue'
</script>