<script lang="ts">

interface Props {
    id: number
    text: string
    completed: boolean
}

const props = defineProps<Props>()

const emit = defineEmits<{
    (e: "toggle", id: number): void
    (e: "remove", id: number): void
}>()

function toggleTask() {
    emit("toggle", props.id)
}

function removeTask() {
    emit("remove", props.id)
}
</script>

<template>
    <li :class="{ completed }">
        <input 
        type="checkbox" 
        :checked="completed" 
        @change="toggleTask"
        >
        <span class="task-text">{{ text }}</span>
        <button class="delete-btn" @click="removeTask">削除</button>
    </li>
</template>

<style scoped>
li {
  display: flex;
  align-items: center;
  padding: 10px;
  border-bottom: 1px solid #eee;
}

.task-text {
  margin: 0 10px;
  flex-grow: 1;
}

.completed .task-text {
  text-decoration: line-through;
  color: #888;
}

.delete-btn {
  background-color: #ff4757;
  color: white;
  border: none;
  border-radius: 4px;
  padding: 4px 8px;
  font-size: 12px;
  cursor: pointer;
}
</style>