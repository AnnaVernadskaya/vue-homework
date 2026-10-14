<script setup>
import Exercise1_1 from './components/Exercise1.1.vue'
import Exercise1_2 from './components/Exercise1.2.vue'
import Exercise1_3 from './components/Exercise1.3.vue'
import Exercise1_4 from './components/Exercise1.4.vue'

import Exercise2_1 from './components/Exercise2.1.vue'
import Exercise2_2 from './components/Exercise2.2.vue'
import Exercise2_3 from './components/Exercise2.3.vue'
import Exercise2_4 from './components/Exercise2.4.vue'
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

@media (max-width: 600px) {
  .homework {
    padding: 16px;
  }

  .exercise {
    padding: 16px;
  }
}
</style>
