<script setup lang="ts">
import { ref, shallowRef, defineAsyncComponent, computed } from 'vue'
import VForLesson from './lessons/01-VFor/VForLesson.vue'
import FormsLesson from './lessons/02-Forms/FormsLesson.vue'

// レッスン一覧の定義
const lessons = [
  { 
    id: 'v-for', 
    name: 'v-forディレクティブ', 
    component: VForLesson
  },
  {
    id: 'v-form',
    name: 'v-form',
    component: FormsLesson
  },
]

// 最初に表示するレッスン
const currentLessonId = ref(lessons[0].id)

// 現在のレッスンコンポーネント
const currentComponent = computed(() => {
  const lesson = lessons.find(l => l.id === currentLessonId.value)
  return lesson ? defineAsyncComponent(lesson.component) : null
})

// レッスンを切り替える関数
function switchLesson(lessonId: string) {
  currentLessonId.value = lessonId
}
</script>

<template>
  <div class="app-container">
    <header>
      <h1>Vue.js 学習記録</h1>
      <nav>
        <ul class="lesson-list">
          <li v-for="lesson in lessons" :key="lesson.id">
            <button 
              @click="switchLesson(lesson.id)"
              :class="{ active: currentLessonId === lesson.id }"
            >
              {{ lesson.name }}
            </button>
          </li>
        </ul>
      </nav>
    </header>
    
    <main>
      <!-- 現在選択されているレッスンをコンポーネントとして表示 -->
      <component :is="currentComponent" />
    </main>
  </div>
</template>