<template>
  <div class="car-card">
    <div class="car-card__header">
      <h3>{{ title }}</h3>
    </div>
    <div class="car-card__content">
      <slot></slot>
    </div>
    <div class="car-card__footer" v-if="$slots.footer">
      <slot name="footer"></slot>
    </div>
  </div>
</template>

<script setup>
defineProps({
  title: {
    type: String,
    required: true
  }
})
</script>

<style scoped>
.car-card {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 16px;
  margin: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.car-card__header h3 {
  margin: 0 0 12px 0;
  color: #333;
}

.car-card__content {
  margin-bottom: 12px;
}

.car-card__footer {
  border-top: 1px solid #eee;
  padding-top: 12px;
}
</style>