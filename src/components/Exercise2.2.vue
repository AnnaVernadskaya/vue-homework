<script setup>
import { ref, computed } from 'vue'

const productName = ref('')
const products = ref([])
let nextId = 1

const productCount = computed(() => products.value.length)

function addProduct() {
  const name = productName.value.trim()

  if (name === '') {
    return
  }

  products.value.push({
    id: nextId++,
    name: name
  })

  productName.value = ''
}

function removeProduct(id) {
  products.value = products.value.filter(product => product.id !== id)
}
</script>

<template>
  <div>
    <form @submit.prevent="addProduct">
      <input
        v-model="productName"
        type="text"
        placeholder="Название покупки"
      >
      <button type="submit">Добавить</button>
    </form>

    <p>Количество элементов: {{ productCount }}</p>

    <p v-if="productCount === 0">Список пуст</p>

    <ul v-else>
      <li v-for="product in products" :key="product.id">
        {{ product.name }}
        <button @click="removeProduct(product.id)">Удалить</button>
      </li>
    </ul>
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
