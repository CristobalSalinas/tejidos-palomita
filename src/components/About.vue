<script setup lang="ts">
const stats = [
  { value: '3+', label: 'Años de experiencia' },
  { value: '100+', label: 'Creaciones realizadas' },
  { value: '50+', label: 'Clientes felices' },
]
</script>

<template>
  <section id="sobre-mi" class="about section">
    <div class="container">
      <div class="about__grid">
        <div class="about__image-wrapper">
          <div class="about__image">
            <span class="about__emoji">👩‍🎨</span>
          </div>
          <div class="about__decoration about__decoration--1"></div>
          <div class="about__decoration about__decoration--2"></div>
        </div>

        <div class="about__content">
          <span class="about__badge">Sobre Mí</span>
          <h2 class="about__title">
            Hola, soy <span class="text-gradient">Isabel</span>
          </h2>
          <p class="about__description">
            Desde pequeña siempre me apasionaron las manualidades y los personajes de 
            mis series y videojuegos favoritos. Un día decidí combinar ambas pasiones 
            y comenzar a crear amigurumis.
          </p>
          <p class="about__description">
            Cada trabajo es único y está hecho con mucho cariño. Me encanta dar vida 
            a los personajes que mis clientes aman, convirtiendo hilos de colores en 
            pequeñas obras de arte que puedes abrazar.
          </p>

          <div class="about__stats">
            <div v-for="stat in stats" :key="stat.label" class="about__stat">
              <span class="about__stat-value">{{ stat.value }}</span>
              <span class="about__stat-label">{{ stat.label }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about__grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--space-3xl);
  align-items: center;
}

.about__image-wrapper {
  position: relative;
  display: flex;
  justify-content: center;
}

.about__image {
  width: 320px;
  height: 320px;
  background: linear-gradient(135deg, var(--color-primary), var(--color-secondary));
  border-radius: var(--radius-xl);
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  z-index: 1;
}

.about__emoji {
  font-size: 8rem;
}

.about__decoration {
  position: absolute;
  border-radius: var(--radius-xl);
  z-index: 0;
}

.about__decoration--1 {
  width: 320px;
  height: 320px;
  background: rgba(126, 206, 199, 0.3);
  top: 20px;
  left: calc(50% - 140px);
}

.about__decoration--2 {
  width: 100px;
  height: 100px;
  background: var(--color-accent);
  bottom: -20px;
  right: calc(50% - 200px);
  border-radius: 50%;
}

.about__content {
  display: flex;
  flex-direction: column;
  gap: var(--space-lg);
}

.about__badge {
  font-family: var(--font-heading);
  font-size: 0.9rem;
  font-weight: 600;
  color: var(--color-primary);
  text-transform: uppercase;
  letter-spacing: 1px;
}

.about__title {
  font-size: clamp(2rem, 4vw, 2.5rem);
}

.about__description {
  font-size: 1.1rem;
  line-height: 1.7;
}

.about__stats {
  display: flex;
  gap: var(--space-xl);
  margin-top: var(--space-lg);
}

.about__stat {
  display: flex;
  flex-direction: column;
}

.about__stat-value {
  font-family: var(--font-heading);
  font-size: 2.5rem;
  font-weight: 700;
  color: var(--color-primary);
}

.about__stat-label {
  font-size: 0.9rem;
  color: var(--text-muted);
}

@media (max-width: 968px) {
  .about__grid {
    grid-template-columns: 1fr;
    text-align: center;
    gap: var(--space-2xl);
  }

  .about__content {
    align-items: center;
  }

  .about__stats {
    justify-content: center;
  }

  .about__image {
    width: 260px;
    height: 260px;
  }

  .about__decoration--1 {
    width: 260px;
    height: 260px;
    left: calc(50% - 110px);
  }

  .about__emoji {
    font-size: 6rem;
  }
}
</style>
