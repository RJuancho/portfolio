<script setup lang="ts">
defineProps<{
  stats: Array<{ value: string; label: string }>
}>()
</script>

<template>
  <section class="stats-section">
    <div class="stats-grid">
      <div v-for="stat in stats" :key="stat.label" class="stat-item">
        <h3>{{ stat.value }}</h3>
        <p>{{ stat.label }}</p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.stats-section {
  margin-bottom: 4rem;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 2rem;
  text-align: center;
}

.stat-item h3 {
  font-size: 2.5rem;
  font-weight: 700;
  color: #667eea;
  margin-bottom: 0.5rem;
}

.stat-item p {
  color: #666;
  font-weight: 500;
}
</style>
