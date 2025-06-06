<template>
  <button
    :class="['car-button', `car-button--${variant}`]"
    @click="$emit('click')"
    :disabled="disabled"
  >
    <slot></slot>
  </button>
</template>

<script setup>
defineEmits(['click'])

defineProps({
  variant: {
    type: String,
    default: 'primary',
    validator: (value) => ['primary', 'secondary', 'danger'].includes(value)
  },
  disabled: {
    type: Boolean,
    default: false
  }
})
</script>

<style scoped>
.car-button {
  padding: 8px 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-weight: 500;
  transition: background-color 0.2s;
}

.car-button--primary {
  background-color: #007bff;
  color: white;
}

.car-button--primary:hover:not(:disabled) {
  background-color: #0056b3;
}

.car-button--secondary {
  background-color: #6c757d;
  color: white;
}

.car-button--secondary:hover:not(:disabled) {
  background-color: #545b62;
}

.car-button--danger {
  background-color: #dc3545;
  color: white;
}

.car-button--danger:hover:not(:disabled) {
  background-color: #c82333;
}

.car-button:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}
</style>