<script setup lang="ts">
import BaseButton from '../ui/BaseButton.vue'

defineProps<{
  title: string
  subtitle: string
  description: string
  yearsExperience: number
}>()

const emit = defineEmits<{
  viewProjects: []
  downloadResume: []
}>()
</script>

<template>
  <section class="hero-section">
    <div class="hero-content">
      <h1 class="hero-title">{{ title }}</h1>
      <h2 class="hero-subtitle">{{ subtitle }}</h2>
      <p class="hero-description">{{ description }}</p>
      <div class="hero-actions">
        <BaseButton variant="primary" @click="emit('viewProjects')"> View My Work </BaseButton>
        <BaseButton variant="secondary" @click="emit('downloadResume')">
          Download Resume
        </BaseButton>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero-section {
  text-align: center;
  padding: 4rem 2rem;
  background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
  border-radius: 20px;
  margin-bottom: 4rem;
}

.hero-title {
  font-size: 3.5rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero-subtitle {
  font-size: 1.8rem;
  color: #4a5568;
  margin-bottom: 1.5rem;
  font-weight: 500;
}

.hero-description {
  font-size: 1.2rem;
  color: #666;
  max-width: 700px;
  margin: 0 auto 2rem;
  line-height: 1.7;
}

.hero-actions {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
}

@media (max-width: 768px) {
  .hero-title {
    font-size: 2.5rem;
  }

  .hero-subtitle {
    font-size: 1.4rem;
  }

  .hero-actions {
    flex-direction: column;
    align-items: center;
  }
}
</style>
