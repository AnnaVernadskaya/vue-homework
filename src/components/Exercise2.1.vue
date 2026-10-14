<script setup>
import { ref } from 'vue'

const grade = ref(0)
</script>

<template>
  <div class="grade-check">
    <label>
      Оценка:
      <input
        v-model.number="grade"
        type="number"
        min="0"
        max="100"
      >
    </label>

    <p
      v-if="grade === '' || grade < 0 || grade > 100"
      class="error"
    >
      Ошибка: число от 0 до 100
    </p>
    <p v-else-if="grade >= 90">Отлично</p>
    <p v-else-if="grade >= 75">Хорошо</p>
    <p v-else-if="grade >= 60">Удовлетворительно</p>
    <p v-else>Не сдал</p>
  </div>
</template>

<style scoped>
.grade-check {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 16px;
}

input {
  width: 80px;
  margin-left: 8px;
  padding: 8px;
  border: 1px solid #aaa;
  border-radius: 4px;
  font: inherit;
}

p {
  margin: 0;
}

.error {
  color: #c62828;
}
</style>
