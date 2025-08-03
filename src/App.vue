<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <nav>
      <RouterLink to="/" class="logo">Ralph Juancho Villaluz</RouterLink>
      <div class="nav-links">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/projects">Projects</RouterLink>
        <RouterLink to="/contact">Contact</RouterLink>
      </div>
    </nav>
  </header>

  <main>
    <RouterView />
  </main>

  <footer>
    <p>&copy; 2025 Your Name. All rights reserved.</p>
  </footer>
</template>

<style scoped>
header {
  background: var(--color-background);
  border-bottom: 1px solid var(--color-border);
  padding: 1rem 0;
}

nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.logo {
  font-size: 1.5rem;
  font-weight: bold;
  text-decoration: none;
}

.nav-links {
  display: flex;
  gap: 2rem;
}

.nav-links a {
  text-decoration: none;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  transition: background-color 0.3s;
}

.nav-links a:hover,
.nav-links a.router-link-active {
  background-color: var(--color-background-soft);
}

main {
  min-height: calc(100vh - 140px);
}

footer {
  background: var(--color-background-soft);
  text-align: center;
  padding: 2rem 0;
  margin-top: 4rem;
}
</style>
