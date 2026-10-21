<script setup>
defineProps({
  name: {
    type: String,
    required: true,
  },
  age: {
    type: Number,
    default: 18,
  },
  role: {
    type: String,
    default: 'Студент',
  },
})
</script>

<template>
  <div class="card">
    <h3>Привет, {{ name }}!</h3>
    <p>Возраст: {{ age }}</p>
    <p>Роль: {{ role }}</p>
  </div>
</template>

<style scoped>
.card {
  padding: 16px;
  margin-bottom: 12px;
  border: 1px solid #369478;
  border-radius: 8px;
}
</style>
