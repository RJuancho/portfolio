<script setup lang="ts">
defineProps<{
  variant?: 'primary' | 'secondary'
  size?: 'small' | 'medium' | 'large'
  disabled?: boolean
}>()

const emit = defineEmits<{
  click: []
}>()
</script>

<template>
  <button
    :class="[
      'base-button',
      `base-button--${variant || 'primary'}`,
      `base-button--${size || 'medium'}`,
    ]"
    :disabled="disabled"
    @click="emit('click')"
  >
    <slot></slot>
  </button>
</template>

<style scoped>
.base-button {
  border: none;
  border-radius: 10px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  text-decoration: none;
  display: inline-block;
}

.base-button--medium {
  padding: 14px 28px;
  font-size: 1rem;
}

.base-button--small {
  padding: 8px 16px;
  font-size: 0.9rem;
}

.base-button--large {
  padding: 18px 36px;
  font-size: 1.1rem;
}

.base-button--primary {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
}

.base-button--primary:hover {
  transform: translateY(-3px);
  box-shadow: 0 10px 30px rgba(102, 126, 234, 0.4);
}

.base-button--secondary {
  background: transparent;
  color: #667eea;
  border: 2px solid #667eea;
}

.base-button--secondary:hover {
  background: #667eea;
  color: white;
  transform: translateY(-2px);
}

.base-button:disabled {
  opacity: 0.6;
  cursor: not-allowed;
  transform: none;
}
</style>
