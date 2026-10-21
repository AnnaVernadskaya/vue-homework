<script setup>
import GreetingCard from './GreetingCard.vue'

const people = [
  { id: 1, name: 'Иван', age: 23, role: 'Разработчик' },
  { id: 2, name: 'Юлия', age: 25, role: 'Преподаватель' },
  { id: 3, name: 'Мария' },
]
</script>

<template>
  <GreetingCard
    v-for="person in people"
    :key="person.id"
    :name="person.name"
    :age="person.age"
    :role="person.role"
  />
</template>
