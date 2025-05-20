<script setup lang="ts">
import { ref } from 'vue';

const tasks = ref([
    { id: 1, name: "Vue.js の学習", completed: false },
    { id: 2, name: "TypeScript の学習", completed: true },
    { id: 3, name: "Vue Router の学習", completed: false },
])

function toggleTask(id: number) {
    const task = tasks.value.find(task => task.id === id)
    if(task) {
        task.completed = !task.completed
    }
}

function addTask() {
    const text = prompt("新しいタスクを入力してください")
    if(text && text.trim()) {
        const newId = Math.max(0, ...tasks.value.map(t => t.id)) + 1
        tasks.value.push({ id: newId, name: text, completed: false})
    }
}

function removeTask(id: number) {
    tasks.value = tasks.value.filter(task => task.id !== id)
}
</script>

<template>
    <div class="lesson">
        <h2>v-for ディレクティブのレッスン</h2>
        <div class="lesson-content">
            <div class="task-controls">
                <button @click="addTask">新しいタスクの追加</button>
            </div>
            <ul class="task-list">
                <TaskItem 
                    v-for="task in tasks" 
                    :key="task.id"
                    :id="task.id"
                    :text="task.text"
                    :completed="task.completed"
                    @toggle="toggleTask"
                    @remove="removeTask"
                />
            </ul>
        </div>
    </div>
</template>

<style lang="css" scoped>
<style scoped>
.lesson {
  font-family: Arial, sans-serif;
}

.lesson-content {
  margin-top: 20px;
}

.task-controls {
  margin-bottom: 20px;
}

.task-list {
  list-style-type: none;
  padding: 0;
}

.task-list li {
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