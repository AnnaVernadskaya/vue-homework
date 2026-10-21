<template>
  <div class="info-box">
    <h3>
      <slot name="header">Информация</slot>
    </h3>

    <div>
      <slot />
    </div>

    <footer v-if="$slots.footer">
      <slot name="footer" />
    </footer>
  </div>
</template>

<style scoped>
.info-box {
  padding: 16px;
  margin-bottom: 12px;
  border: 1px solid #369478;
  border-radius: 8px;
}

footer {
  margin-top: 12px;
  color: #666;
}
</style>
