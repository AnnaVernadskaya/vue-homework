<script setup>
import { ref } from 'vue'

const props = defineProps({
  label: {
    type: String,
    required: true,
  },
  step: {
    type: Number,
    default: 1,
  },
})

const count = ref(0)

const emit = defineEmits(['change'])

function increase() {
  count.value += props.step
  emit('change', count.value)
}
</script>

<template>
  <button @click="increase">
    {{ label }}: {{ count }}
  </button>
</template>
