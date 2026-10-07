<script setup>
import { ref } from 'vue'

const title = ref('Анна Вернадская')
const university = 'НИТУ МИСИС'
const course = 'Веб-разработка'

function changeTitle() {
  title.value = 'Заголовок изменён'
}
</script>

<template>
  <h1>{{ title }}</h1>

  <p>{{ university }}</p>
  <p>{{ course }}</p>

  <button @click="changeTitle">Изменить заголовок</button>
</template>

<style scoped>

</style>
