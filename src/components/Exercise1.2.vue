<script setup>
import { ref } from 'vue'

const count = ref(0)
const step = ref(1)

function increase() {
  count.value = Math.min(count.value + step.value, 20)
}

function decrease() {
  count.value = Math.max(count.value - step.value, 0)
}
</script>

<template>
  <section>
    <h2>Счётчик</h2>

    <p>Значение: {{ count }}</p>

    <button @click="decrease" :disabled="count === 0">
      Уменьшить
    </button>

    <button @click="increase" :disabled="count === 20">
      Увеличить
    </button>

    <div>
      <label>
        Шаг:
        <input v-model.number="step" type="number" min="1">
      </label>
    </div>
  </section>
</template>
