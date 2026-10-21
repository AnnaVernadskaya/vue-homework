<script setup>
import { ref, computed } from 'vue'
import CounterButton from './CounterButton.vue'

const apples = ref(0)
const pears = ref(0)

const total = computed(() => apples.value + pears.value)

function updateApples(value) {
  apples.value = value
}

function updatePears(value) {
  pears.value = value
}
</script>

<template>
  <div>
    <CounterButton
      label="Яблоки"
      @change="updateApples"
    />

    <CounterButton
      label="Груши"
      :step="5"
      @change="updatePears"
    />

    <p>Всего: {{ total }}</p>
  </div>
</template>
