<script setup>
import { ref, computed } from 'vue'

const search = ref('')
const selectedCategory = ref('Все')

const courses = ref([
  { id: 1, title: 'Основы Vue', category: 'Программирование' },
  { id: 2, title: 'JavaScript', category: 'Программирование' },
  { id: 3, title: 'Веб-дизайн', category: 'Дизайн' },
  { id: 4, title: 'Основы Figma', category: 'Дизайн' },
  { id: 5, title: 'Анализ данных', category: 'Данные' },
  { id: 6, title: 'Базы данных', category: 'Данные' }
])

const filteredCourses = computed(() => {
  const query = search.value.trim().toLowerCase()

  return courses.value.filter(course => {
    const matchesTitle = course.title.toLowerCase().includes(query)
    const matchesCategory =
      selectedCategory.value === 'Все' ||
      course.category === selectedCategory.value

    return matchesTitle && matchesCategory
  })
})
</script>

<template>
  <div>
    <input
      v-model="search"
      type="text"
      placeholder="Поиск по названию"
    >

    <select v-model="selectedCategory">
      <option>Все</option>
      <option>Программирование</option>
      <option>Дизайн</option>
      <option>Данные</option>
    </select>

    <ul v-if="filteredCourses.length > 0">
      <li v-for="course in filteredCourses" :key="course.id">
        {{ course.title }} — {{ course.category }}
      </li>
    </ul>

    <p v-else>Ничего не найдено.</p>
  </div>
</template>

<style scoped>
input {
  margin-right: 8px;
}

li {
  margin-bottom: 8px;
}
</style>
