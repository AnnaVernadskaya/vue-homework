<script setup>
import { ref } from 'vue'

const username = ref('')
</script>

<template>
  <section>
    <h2>Регистрация</h2>

    <input
      v-model="username"
      type="text"
      placeholder="Введите имя"
    >

    <p>Привет, {{ username }}!</p>

    <p :class="{ warning: username.length >= 12 }">
      Количество символов: {{ username.length }}
    </p>

    <button :disabled="username.length < 4">
      Регистрация
    </button>
  </section>
</template>

<style scoped>
.warning {
  color: red;
}
</style>
