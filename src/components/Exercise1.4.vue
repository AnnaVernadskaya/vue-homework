<script setup>
import { ref } from 'vue'

const isDark = ref(false)

function toggleTheme() {
  isDark.value = !isDark.value
}
</script>

<template>
  <section>
    <h2>Смена режима</h2>

    <div :class="{ dark: isDark, light: !isDark }">
      <p>Это блок с текстом.</p>
    </div>

    <button @click="toggleTheme">
      {{ isDark ? 'Включить светлый режим' : 'Включить тёмный режим' }}
    </button>
  </section>
</template>

<style scoped>
div {
  padding: 20px;
  margin-bottom: 10px;
}

.light {
  background-color: white;
  color: black;
}

.dark {
  background-color: #222;
  color: white;
}
</style>
