<script setup>
import { ref, computed } from 'vue'

const students = ref([
  { id: 1, name: 'Роман', grade: 90 },
  { id: 2, name: 'Иван', grade: 75 },
  { id: 3, name: 'Мария', grade: 55 }
])

const maxGrade = computed(() => {
  if (students.value.length === 0) {
    return '—'
  }

  return Math.max(...students.value.map(student => student.grade))
})

const minGrade = computed(() => {
  if (students.value.length === 0) {
    return '—'
  }

  return Math.min(...students.value.map(student => student.grade))
})

const averageGrade = computed(() => {
  if (students.value.length === 0) {
    return '—'
  }

  const total = students.value.reduce((sum, student) => {
    return sum + student.grade
  }, 0)

  return (total / students.value.length).toFixed(1)
})

const passedCount = computed(() => {
  return students.value.filter(student => student.grade >= 60).length
})

function increaseGrade(student) {
  student.grade = Math.min(student.grade + 5, 100)
}

function decreaseGrade(student) {
  student.grade = Math.max(student.grade - 5, 0)
}
</script>

<template>
  <div>
    <p>Максимальная оценка: {{ maxGrade }}</p>
    <p>Минимальная оценка: {{ minGrade }}</p>
    <p>Средняя оценка: {{ averageGrade }}</p>
    <p>Количество сдавших: {{ passedCount }}</p>

    <ul v-if="students.length > 0">
      <li v-for="student in students" :key="student.id">
        {{ student.name }}: {{ student.grade }}

        <button
          @click="increaseGrade(student)"
          :disabled="student.grade === 100"
        >
          +5
        </button>

        <button
          @click="decreaseGrade(student)"
          :disabled="student.grade === 0"
        >
          -5
        </button>
      </li>
    </ul>

    <p v-else>Список пуст</p>
  </div>
</template>

<style scoped>
li {
  margin-bottom: 12px;
}

button {
  margin-left: 8px;
}
</style>
