<script setup lang="ts">
const props = defineProps<{
    name: string
}>()
</script>

<template>
    <p>こんにちは、{{ props.name }} さん！！！</p>
</template>

