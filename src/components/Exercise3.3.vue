<script setup>
import InfoBox from './InfoBox.vue'
</script>

<template>
  <div>
    <InfoBox>
      <p>Это блок с заголовком по умолчанию.</p>
    </InfoBox>

    <InfoBox>
      <template #header>Новости курса</template>

      <p>Сегодня изучаем слоты во Vue.</p>
    </InfoBox>

    <InfoBox>
      <template #header>Домашнее задание</template>

      <p>Нужно выполнить упражнение с компонентом InfoBox.</p>

      <template #footer>Срок сдачи — пятница.</template>
    </InfoBox>
  </div>
</template>
