<script setup>
defineProps({
  todo: {
    type: Object,
    required: true,
  },
})

const emit = defineEmits(['toggle', 'remove'])
</script>

<template>
  <li class="todo-item">
    <label>
      <input
        type="checkbox"
        :checked="todo.done"
        @change="emit('toggle', todo.id)"
      />

      <span :class="{ done: todo.done }">
        {{ todo.title }}
      </span>
    </label>

    <button @click="emit('remove', todo.id)">
      Удалить
    </button>
  </li>
</template>

<style scoped>
.todo-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 12px;
  margin-bottom: 12px;
}

.done {
  text-decoration: line-through;
  color: #888;
}
</style>
