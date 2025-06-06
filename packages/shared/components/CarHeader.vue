<template>
  <header class="car-header">
    <div class="car-header__logo">
      <slot name="logo">
        <h1>🚗 {{ appName }}</h1>
      </slot>
    </div>
    <nav class="car-header__nav" v-if="$slots.nav">
      <slot name="nav"></slot>
    </nav>
  </header>
</template>

<script setup>
defineProps({
  appName: {
    type: String,
    default: 'Car App'
  }
})
</script>

<style scoped>
.car-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 16px 24px;
  background-color: #f8f9fa;
  border-bottom: 1px solid #dee2e6;
}

.car-header__logo h1 {
  margin: 0;
  color: #333;
  font-size: 1.5rem;
}

.car-header__nav {
  display: flex;
  gap: 16px;
}
</style>