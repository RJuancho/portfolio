<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import { ref } from 'vue'

const isMobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const closeMobileMenu = () => {
  isMobileMenuOpen.value = false
}
</script>

<template>
  <header>
    <nav>
      <!-- Move Mobile Hamburger Button to the beginning -->
      <button
        class="mobile-menu-btn"
        @click="toggleMobileMenu"
        :aria-expanded="isMobileMenuOpen"
        aria-label="Toggle navigation menu"
      >
        <span class="hamburger-line" :class="{ active: isMobileMenuOpen }"></span>
        <span class="hamburger-line" :class="{ active: isMobileMenuOpen }"></span>
        <span class="hamburger-line" :class="{ active: isMobileMenuOpen }"></span>
      </button>

      <RouterLink to="/" class="logo" @click="closeMobileMenu">Ralph Juancho</RouterLink>

      <!-- Desktop Navigation -->
      <div class="nav-links desktop-nav">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/projects">Projects</RouterLink>
        <RouterLink to="/contact">Contact</RouterLink>
      </div>
    </nav>

    <!-- Mobile Navigation Menu -->
    <div class="mobile-nav" :class="{ open: isMobileMenuOpen }">
      <div class="mobile-nav-links">
        <RouterLink to="/" @click="closeMobileMenu">Home</RouterLink>
        <RouterLink to="/about" @click="closeMobileMenu">About</RouterLink>
        <RouterLink to="/projects" @click="closeMobileMenu">Projects</RouterLink>
        <RouterLink to="/contact" @click="closeMobileMenu">Contact</RouterLink>
      </div>
    </div>

    <!-- Mobile Menu Overlay -->
    <div
      class="mobile-menu-overlay"
      :class="{ open: isMobileMenuOpen }"
      @click="closeMobileMenu"
    ></div>
  </header>

  <main>
    <RouterView />
  </main>

  <footer>
    <p>&copy; 2025 Ralph Juancho Villaluz. All rights reserved.</p>
  </footer>
</template>

<style scoped>
header {
  background: var(--color-background);
  border-bottom: 1px solid var(--color-border);
  padding: 1rem 0;
  position: relative;
  z-index: 1000;
}

nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
  position: relative;
}

/* Mobile Menu Button */
.mobile-menu-btn {
  display: none;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 44px;
  height: 44px;
  background: transparent;
  border: none;
  cursor: pointer;
  padding: 8px;
  z-index: 1001;
  position: relative;
}

.hamburger-line {
  width: 24px;
  height: 2px;
  background-color: var(--color-text);
  transition: all 0.3s ease;
  transform-origin: center;
  margin: 2px 0;
}

.hamburger-line.active:nth-child(1) {
  transform: rotate(45deg) translate(6px, 6px);
}

.hamburger-line.active:nth-child(2) {
  opacity: 0;
}

.hamburger-line.active:nth-child(3) {
  transform: rotate(-45deg) translate(6px, -6px);
}

/* Mobile Navigation */
.mobile-nav {
  position: fixed;
  top: 0;
  right: -100%;
  width: 280px;
  height: 100vh;
  background: var(--color-background);
  border-left: 1px solid var(--color-border);
  transition: right 0.3s ease;
  z-index: 999;
  padding-top: 80px;
  box-shadow: -2px 0 10px rgba(0, 0, 0, 0.1);
}

.mobile-nav.open {
  right: 0;
}

.mobile-nav-links {
  display: flex;
  flex-direction: column;
  padding: 2rem 1.5rem;
  gap: 0.5rem;
}

.mobile-nav-links a {
  text-decoration: none;
  padding: 1rem 1.5rem;
  border-radius: 8px;
  transition: all 0.3s ease;
  color: var(--color-text);
  font-weight: 500;
  font-size: 1.1rem;
  border: 2px solid transparent;
}

.mobile-nav-links a:hover,
.mobile-nav-links a.router-link-active {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  transform: translateX(-2px);
  border-color: rgba(255, 255, 255, 0.2);
}

/* Mobile Menu Overlay */
.mobile-menu-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(0, 0, 0, 0.5);
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s ease;
  z-index: 998;
}

.mobile-menu-overlay.open {
  opacity: 1;
  visibility: visible;
}

main {
  min-height: calc(100vh - 140px);
}

footer {
  background: var(--color-background-soft);
  text-align: center;
  padding: 2rem 0;
  margin-top: 4rem;
  color: var(--color-text);
}

/* Responsive Design */
@media (max-width: 768px) {
  nav {
    padding: 0 1rem;
    /* Change to flex-start when mobile menu is shown */
    justify-content: flex-start;
    flex-direction: row;
    align-items: left;
    gap: 1rem;
  }

  .logo {
    font-size: 1.3rem;
    /* Allow logo to take remaining space */
    flex: 1;
  }

  .desktop-nav {
    display: none;
  }

  .mobile-menu-btn {
    display: flex;
  }
}

@media (max-width: 480px) {
  nav {
    padding: 0 0.75rem;
    flex-direction: row;
    align-items: left;
  }

  .logo {
    font-size: 1.2rem;
    max-width: 200px;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }

  .mobile-nav {
    width: 100vw;
    right: -100vw;
  }

  .mobile-nav.open {
    right: 0;
  }

  .mobile-nav-links {
    padding: 2rem 1rem;
  }

  .mobile-nav-links a {
    padding: 0.875rem 1.25rem;
    font-size: 1rem;
  }
}

@media (max-width: 360px) {
  .logo {
    font-size: 1.1rem;
    max-width: 180px;
  }

  .mobile-nav-links {
    padding: 1.5rem 0.75rem;
  }

  .mobile-nav-links a {
    padding: 0.75rem 1rem;
    font-size: 0.95rem;
  }
}

/* Touch device optimizations */
@media (hover: none) and (pointer: coarse) {
  .nav-links a:hover {
    background: none;
    color: var(--color-text);
    transform: none;
    box-shadow: none;
  }

  .mobile-nav-links a:hover {
    background: none;
    color: var(--color-text);
    transform: none;
    border-color: transparent;
  }

  /* Keep active states for touch devices */
  .nav-links a.router-link-active,
  .mobile-nav-links a.router-link-active {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
  }

  /* Add touch feedback */
  .mobile-menu-btn:active {
    background: rgba(0, 0, 0, 0.1);
  }

  .mobile-nav-links a:active {
    background: rgba(102, 126, 234, 0.1);
  }
}

/* Prevent body scroll when menu is open */
body:has(.mobile-nav.open) {
  overflow: hidden;
}

/* Accessibility improvements */
@media (prefers-reduced-motion: reduce) {
  .mobile-nav,
  .hamburger-line,
  .mobile-menu-overlay,
  .nav-links a,
  .mobile-nav-links a {
    transition: none;
  }
}

/* Focus states for accessibility */
.mobile-menu-btn:focus {
  outline: 2px solid var(--vt-c-text-1);
  outline-offset: 2px;
}

.nav-links a:focus,
.mobile-nav-links a:focus {
  outline: 2px solid var(--vt-c-text-1);
  outline-offset: 2px;
}
</style>
