<template>
  <div class="task-item">
    <header>
      <h3>{{ props.task.title }}</h3>
    </header>
    <main>
      <p>{{ props.task.text }}</p>
    </main>
    <footer>
      <small>ID: {{ props.task.id }}</small>
    </footer>
  </div>
</template>

<script setup lang="ts">
// Определяем интерфейс для задачи
interface Task {
  id: number;
  title: string;
  text: string;
}

// Определяем props
const props = defineProps<{
  task: Task;
}>();
</script>

<style scoped>
.task-item {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 16px;
  margin: 8px 0;
  background-color: #f9f9f9;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.task-item header h3 {
  margin: 0 0 8px 0;
  color: #333;
}

.task-item main p {
  margin: 0 0 8px 0;
  color: #666;
}

.task-item footer small {
  color: #999;
}
</style>