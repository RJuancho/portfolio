<script setup lang="ts">
defineProps<{
  tags: string[]
  variant?: 'primary' | 'secondary'
}>()
</script>

<template>
  <div class="tag-list">
    <span v-for="tag in tags" :key="tag" :class="['tag', `tag--${variant || 'primary'}`]">
      {{ tag }}
    </span>
  </div>
</template>

<style scoped>
.tag-list {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tag {
  padding: 0.4rem 0.8rem;
  border-radius: 15px;
  font-size: 0.85rem;
  font-weight: 500;
}

.tag--primary {
  background: #667eea;
  color: white;
}

.tag--secondary {
  background: #e2e8f0;
  color: #4a5568;
}
</style>
