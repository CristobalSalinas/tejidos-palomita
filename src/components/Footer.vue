<script setup lang="ts">
const currentYear = new Date().getFullYear()

const navLinks = [
  { href: '#inicio', label: 'Inicio' },
  { href: '#galeria', label: 'Galería' },
  { href: '#sobre-mi', label: 'Sobre Mí' },
  { href: '#contacto', label: 'Contacto' },
]

const socialLinks = [
  { name: 'Instagram', icon: '📸', url: '#' },
  { name: 'Facebook', icon: '👍', url: '#' },
  { name: 'WhatsApp', icon: '💬', url: '#' },
]
</script>

<template>
  <footer class="footer">
    <div class="container">
      <div class="footer__content">
        <div class="footer__brand">
          <a href="#inicio" class="footer__logo">
            <span class="footer__logo-icon">🧶</span>
            <span class="footer__logo-text">Tejidos Palomita</span>
          </a>
          <p class="footer__tagline">
            Creando personajes de tus mundos favoritos, tejidos con amor.
          </p>
        </div>

        <nav class="footer__nav">
          <h4 class="footer__nav-title">Enlaces</h4>
          <ul class="footer__nav-list">
            <li v-for="link in navLinks" :key="link.href">
              <a :href="link.href" class="footer__nav-link">{{ link.label }}</a>
            </li>
          </ul>
        </nav>

        <div class="footer__social">
          <h4 class="footer__nav-title">Sígueme</h4>
          <div class="footer__social-links">
            <a
              v-for="link in socialLinks"
              :key="link.name"
              :href="link.url"
              class="footer__social-link"
              :title="link.name"
            >
              {{ link.icon }}
            </a>
          </div>
        </div>
      </div>

      <div class="footer__bottom">
        <p>&copy; {{ currentYear }} Tejidos Palomita. Todos los derechos reservados.</p>
        <p class="footer__made-with">Hecho con 💖 y mucho 🧶</p>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background: var(--bg-dark);
  color: var(--text-light);
  padding: var(--space-3xl) 0 var(--space-xl);
}

.footer__content {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr;
  gap: var(--space-2xl);
  padding-bottom: var(--space-2xl);
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.footer__brand {
  max-width: 300px;
}

.footer__logo {
  display: inline-flex;
  align-items: center;
  gap: var(--space-sm);
  font-family: var(--font-heading);
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--text-light);
  text-decoration: none;
  margin-bottom: var(--space-md);
}

.footer__logo-icon {
  font-size: 2rem;
}

.footer__logo-text {
  background: linear-gradient(135deg, var(--color-primary), var(--color-secondary));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.footer__tagline {
  color: rgba(255, 255, 255, 0.7);
  font-size: 0.95rem;
  line-height: 1.6;
}

.footer__nav-title {
  font-family: var(--font-heading);
  font-size: 1rem;
  font-weight: 600;
  margin-bottom: var(--space-md);
  color: var(--text-light);
}

.footer__nav-list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: var(--space-sm);
}

.footer__nav-link {
  color: rgba(255, 255, 255, 0.7);
  text-decoration: none;
  font-size: 0.95rem;
  transition: color var(--transition-fast);
}

.footer__nav-link:hover {
  color: var(--color-primary);
}

.footer__social-links {
  display: flex;
  gap: var(--space-md);
}

.footer__social-link {
  width: 44px;
  height: 44px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 50%;
  font-size: 1.25rem;
  text-decoration: none;
  transition: all var(--transition-base);
}

.footer__social-link:hover {
  background: var(--color-primary);
  transform: translateY(-2px);
}

.footer__bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: var(--space-xl);
  font-size: 0.9rem;
  color: rgba(255, 255, 255, 0.5);
}

.footer__made-with {
  color: rgba(255, 255, 255, 0.7);
}

@media (max-width: 768px) {
  .footer__content {
    grid-template-columns: 1fr;
    text-align: center;
  }

  .footer__brand {
    max-width: 100%;
  }

  .footer__logo {
    justify-content: center;
  }

  .footer__nav-list {
    flex-direction: row;
    justify-content: center;
    flex-wrap: wrap;
    gap: var(--space-md);
  }

  .footer__social-links {
    justify-content: center;
  }

  .footer__bottom {
    flex-direction: column;
    gap: var(--space-sm);
    text-align: center;
  }
}
</style>
