<script setup>
import { computed } from 'vue'
import { RouterLink } from 'vue-router'

const props = defineProps({
  to: {
    type: String,
    default: ''
  },
  variant: {
    type: String,
    default: 'primary' // 'primary', 'secondary', 'outline'
  },
  icon: {
    type: Boolean,
    default: false
  }
})

const isLink = computed(() => !!props.to)
</script>

<template>
  <component 
    :is="isLink ? RouterLink : 'button'" 
    :to="isLink ? to : undefined"
    :class="['btn', `btn-${variant}`, { 'has-icon': icon }]"
  >
    <slot></slot>
  </component>
</template>

<style scoped>
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  padding: 12px 24px;
  border-radius: var(--border-radius);
  font-weight: 600;
  font-size: 14px;
  border: none;
  transition: all 0.3s ease;
  white-space: nowrap;
}

.btn-primary {
  background-color: var(--color-primary);
  color: white;
}

.btn-primary:hover {
  background-color: var(--color-primary-dark);
  box-shadow: var(--shadow-md);
  transform: translateY(-2px);
}

.btn-outline {
  background-color: transparent;
  color: var(--color-primary);
  border: 1px solid var(--color-primary);
}

.btn-outline:hover {
  background-color: var(--color-surface);
  transform: translateY(-2px);
}

.btn-white {
  background-color: white;
  color: var(--color-primary);
}

.btn-white:hover {
  background-color: var(--color-surface);
  box-shadow: var(--shadow-md);
  transform: translateY(-2px);
}
</style>
