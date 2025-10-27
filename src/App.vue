<template>
  <div class="app">
    <header class="app-header">
      <h1>Мой список дел</h1>
      <p>Всего задач: {{ tasksCount }}</p>
    </header>
    
    <main class="tasks-container">
      <div v-if="tasks.length === 0" class="no-tasks">
        <p>Задач пока нет. Добавьте первую задачу!</p>
      </div>
      
      <div v-else class="tasks-list">
        <TaskItem
          v-for="task in tasks"
          :key="task.id"
          :task="task"
        />
      </div>
    </main>
  </div>
</template>

<script setup lang="ts">
import { computed } from "vue";
import TaskItem from "./components/TaskItem.vue";

// Интерфейс для задачи
interface Task {
  id: number;
  title: string;
  text: string;
}

// Массив дел
const tasks = [
  { id: 1, title: "Изучить Vue 3", text: "Освоить основы Vue 3 и Composition API" },
  { id: 2, title: "Создать ToDo приложение", text: "Реализовать функционал списка дел" },
  { id: 3, title: "Изучить TypeScript", text: "Разобраться с типами в TypeScript" },
  { id: 4, title: "Деплой проекта", text: "Задеплоить приложение на хостинг" },
  { id: 5, title: "Написать тесты", text: "Добавить unit-тесты для компонентов" }
];

// Computed свойство для подсчета количества задач
const tasksCount = computed(() => {
  return tasks.length;
});
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.app-header {
  text-align: center;
  margin-bottom: 30px;
  padding: 20px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border-radius: 10px;
}

.app-header h1 {
  margin-bottom: 10px;
  font-size: 2.5rem;
}

.tasks-container {
  min-height: 400px;
}

.no-tasks {
  text-align: center;
  padding: 40px;
  background-color: #f8f9fa;
  border-radius: 8px;
  color: #6c757d;
}

.tasks-list {
  display: flex;
  flex-direction: column;
  gap: 12px;
}
</style>