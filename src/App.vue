<script setup>
import { ref, computed } from 'vue'
import TodoItem from './components/TodoItem.vue'
import { useLocalStorage } from './composables/useLocalStorage.js'

import Exercise1_1 from './components/Exercise1.1.vue'
import Exercise1_2 from './components/Exercise1.2.vue'
import Exercise1_3 from './components/Exercise1.3.vue'
import Exercise1_4 from './components/Exercise1.4.vue'

import Exercise2_1 from './components/Exercise2.1.vue'
import Exercise2_2 from './components/Exercise2.2.vue'
import Exercise2_3 from './components/Exercise2.3.vue'
import Exercise2_4 from './components/Exercise2.4.vue'

import Exercise3_1 from './components/Exercise3.1.vue'
import Exercise3_2 from './components/Exercise3.2.vue'
import Exercise3_3 from './components/Exercise3.3.vue'

const newTitle = ref('')

const todos = useLocalStorage('vue-homework-todos', [])

const remaining = computed(() => {
  return todos.value.filter((todo) => !todo.done).length
})

const hasCompleted = computed(() => {
  return todos.value.some((todo) => todo.done)
})

function addTodo() {
  const title = newTitle.value.trim()

  if (title === '') {
    return
  }

  todos.value.push({
    id: Date.now(),
    title: title,
    done: false,
  })

  newTitle.value = ''
}

function toggleTodo(id) {
  const todo = todos.value.find((todo) => todo.id === id)

  if (todo) {
    todo.done = !todo.done
  }
}

function removeTodo(id) {
  todos.value = todos.value.filter((todo) => todo.id !== id)
}

function clearCompleted() {
  todos.value = todos.value.filter((todo) => !todo.done)
}
</script>

<template>
  <main class="homework">
    <h1>Домашние задания по Vue</h1>

    <section class="lesson">
      <h2>Занятие 1</h2>

      <div class="exercise">
        <h3>Упражнение 1. Приветствие</h3>
        <Exercise1_1 />
      </div>

      <div class="exercise">
        <h3>Упражнение 2. Счётчик</h3>
        <Exercise1_2 />
      </div>

      <div class="exercise">
        <h3>Упражнение 3. Ввод имени</h3>
        <Exercise1_3 />
      </div>

      <div class="exercise">
        <h3>Упражнение 4. Смена режима</h3>
        <Exercise1_4 />
      </div>
    </section>

    <section class="lesson">
      <h2>Занятие 2</h2>

      <div class="exercise">
        <h3>Упражнение 1. Оценка словами</h3>
        <Exercise2_1 />
      </div>

      <div class="exercise">
        <h3>Упражнение 2. Список покупок</h3>
        <Exercise2_2 />
      </div>

      <div class="exercise">
        <h3>Упражнение 3. Каталог курсов</h3>
        <Exercise2_3 />
      </div>

      <div class="exercise">
        <h3>Упражнение 4. Статистика оценок</h3>
        <Exercise2_4 />
      </div>
    </section>

    <section class="lesson">
      <h2>Занятие 3</h2>

      <div class="exercise">
        <h3>Упражнение 1. Карточка приветствия</h3>
        <Exercise3_1 />
      </div>

      <div class="exercise">
        <h3>Упражнение 2. Счётчик с событием</h3>
        <Exercise3_2 />
      </div>

      <div class="exercise">
        <h3>Упражнение 3. Блок со слотами</h3>
        <Exercise3_3 />
      </div>

      <div class="exercise">
        <h3>Упражнение 4. Список задач из компонентов</h3>

        <form class="todo-form" @submit.prevent="addTodo">
          <input
            v-model="newTitle"
            aria-label="Новая задача"
            placeholder="Новая задача"
          />

          <button type="submit">Добавить</button>
        </form>

        <p>Осталось: {{ remaining }}</p>

        <ul class="todo-list">
          <TodoItem
            v-for="todo in todos"
            :key="todo.id"
            :todo="todo"
            @toggle="toggleTodo"
            @remove="removeTodo"
          />
        </ul>

        <button
          v-if="hasCompleted"
          @click="clearCompleted"
        >
          Очистить выполненные
        </button>
      </div>
    </section>
  </main>
</template>

<style scoped>
.homework {
  max-width: 900px;
  margin: 0 auto;
  padding: 24px;
  font-family: Arial, sans-serif;
  color: #222;
}

.lesson {
  margin-top: 40px;
}

.lesson > h2 {
  padding-bottom: 12px;
  border-bottom: 2px solid #369478;
}

.exercise {
  margin-top: 20px;
  padding: 24px;
  border: 1px solid #d5d5d5;
  border-radius: 8px;
  background-color: #fff;
}

.exercise > h3 {
  margin: 0 0 20px;
  font-size: 16px;
  font-weight: 600;
  color: #555;
}

.todo-form {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.todo-form input {
  flex: 1;
  min-width: 0;
  padding: 8px;
}

.todo-form button {
  padding: 8px 12px;
}

.todo-list {
  padding: 0;
  list-style: none;
}

@media (max-width: 600px) {
  .homework {
    padding: 16px;
  }

  .exercise {
    padding: 16px;
  }
}
</style>
