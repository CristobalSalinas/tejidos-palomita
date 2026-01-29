<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const isMobileMenuOpen = ref(false)

const navLinks = [
  { href: '#inicio', label: 'Inicio' },
  { href: '#galeria', label: 'Galería' },
  { href: '#sobre-mi', label: 'Sobre Mí' },
  { href: '#contacto', label: 'Contacto' },
]

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const closeMobileMenu = () => {
  isMobileMenuOpen.value = false
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <header class="header" :class="{ 'header--scrolled': isScrolled }">
    <div class="header__container container">
      <a href="#inicio" class="header__logo">
        <span class="header__logo-icon">🧶</span>
        <span class="header__logo-text">Tejidos Palomita</span>
      </a>

      <nav class="header__nav" :class="{ 'header__nav--open': isMobileMenuOpen }">
        <a
          v-for="link in navLinks"
          :key="link.href"
          :href="link.href"
          class="header__link"
          @click="closeMobileMenu"
        >
          {{ link.label }}
        </a>
      </nav>

      <button
        class="header__menu-btn"
        @click="toggleMobileMenu"
        :aria-expanded="isMobileMenuOpen"
        aria-label="Menú de navegación"
      >
        <span class="header__menu-icon" :class="{ 'header__menu-icon--open': isMobileMenuOpen }"></span>
      </button>
    </div>
  </header>
</template>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  padding: var(--space-md) 0;
  transition: all var(--transition-base);
  background: transparent;
}

.header--scrolled {
  background: rgba(255, 249, 245, 0.95);
  backdrop-filter: blur(10px);
  box-shadow: var(--shadow-sm);
  padding: var(--space-sm) 0;
}

.header__container {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.header__logo {
  display: flex;
  align-items: center;
  gap: var(--space-sm);
  font-family: var(--font-heading);
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--text-dark);
  text-decoration: none;
}

.header__logo-icon {
  font-size: 2rem;
}

.header__logo-text {
  background: linear-gradient(135deg, var(--color-primary), var(--color-secondary));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.header__nav {
  display: flex;
  align-items: center;
  gap: var(--space-xl);
}

.header__link {
  font-family: var(--font-heading);
  font-weight: 600;
  color: var(--text-dark);
  text-decoration: none;
  padding: var(--space-sm) 0;
  position: relative;
  transition: color var(--transition-fast);
}

.header__link::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 2px;
  background: linear-gradient(135deg, var(--color-primary), var(--color-secondary));
  transition: width var(--transition-base);
}

.header__link:hover {
  color: var(--color-primary);
}

.header__link:hover::after {
  width: 100%;
}

.header__menu-btn {
  display: none;
  background: none;
  border: none;
  cursor: pointer;
  padding: var(--space-sm);
}

.header__menu-icon {
  display: block;
  width: 24px;
  height: 2px;
  background: var(--text-dark);
  position: relative;
  transition: background var(--transition-fast);
}

.header__menu-icon::before,
.header__menu-icon::after {
  content: '';
  position: absolute;
  width: 24px;
  height: 2px;
  background: var(--text-dark);
  transition: transform var(--transition-base);
}

.header__menu-icon::before {
  top: -7px;
}

.header__menu-icon::after {
  bottom: -7px;
}

.header__menu-icon--open {
  background: transparent;
}

.header__menu-icon--open::before {
  transform: rotate(45deg) translate(5px, 5px);
}

.header__menu-icon--open::after {
  transform: rotate(-45deg) translate(5px, -5px);
}

@media (max-width: 768px) {
  .header__menu-btn {
    display: block;
  }

  .header__nav {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    flex-direction: column;
    justify-content: center;
    gap: var(--space-xl);
    background: var(--bg-light);
    transform: translateX(100%);
    transition: transform var(--transition-base);
  }

  .header__nav--open {
    transform: translateX(0);
  }

  .header__link {
    font-size: 1.5rem;
  }
}
</style>
