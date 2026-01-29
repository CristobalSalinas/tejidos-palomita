<script setup lang="ts">
</script>

<template>
  <section id="inicio" class="hero">
    <div class="hero__bg">
      <div class="hero__shape hero__shape--1"></div>
      <div class="hero__shape hero__shape--2"></div>
      <div class="hero__shape hero__shape--3"></div>
    </div>
    
    <div class="hero__container container">
      <div class="hero__content">
        <span class="hero__badge animate-fadeInUp">✨ Hecho a mano con amor</span>
        <h1 class="hero__title animate-fadeInUp">
          Creando personajes de tus 
          <span class="text-gradient">mundos favoritos</span>
        </h1>
        <p class="hero__description animate-fadeInUp">
          Transformo tus personajes favoritos de videojuegos, anime y series en 
          adorables amigurumis únicos. Cada creación es tejida con dedicación y cariño.
        </p>
        <div class="hero__actions animate-fadeInUp">
          <a href="#galeria" class="btn btn-primary">
            Ver Galería
            <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M5 12h14M12 5l7 7-7 7"/>
            </svg>
          </a>
          <a href="#contacto" class="btn btn-secondary">Contactar</a>
        </div>
      </div>

      <div class="hero__visual animate-float">
        <div class="hero__image-container">
          <div class="hero__yarn hero__yarn--1">🧶</div>
          <div class="hero__yarn hero__yarn--2">🪡</div>
          <div class="hero__character">🐰</div>
          <div class="hero__yarn hero__yarn--3">✨</div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  position: relative;
  overflow: hidden;
  padding-top: 80px;
}

.hero__bg {
  position: absolute;
  inset: 0;
  overflow: hidden;
  z-index: -1;
}

.hero__shape {
  position: absolute;
  border-radius: 50%;
  filter: blur(60px);
  opacity: 0.4;
}

.hero__shape--1 {
  width: 400px;
  height: 400px;
  background: var(--color-primary);
  top: -100px;
  right: -100px;
}

.hero__shape--2 {
  width: 300px;
  height: 300px;
  background: var(--color-secondary);
  bottom: -50px;
  left: -50px;
}

.hero__shape--3 {
  width: 200px;
  height: 200px;
  background: var(--color-accent);
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.hero__container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--space-3xl);
  align-items: center;
}

.hero__content {
  display: flex;
  flex-direction: column;
  gap: var(--space-lg);
}

.hero__badge {
  display: inline-flex;
  align-items: center;
  gap: var(--space-sm);
  background: white;
  padding: var(--space-sm) var(--space-md);
  border-radius: var(--radius-full);
  font-size: 0.9rem;
  font-weight: 600;
  color: var(--color-primary);
  box-shadow: var(--shadow-sm);
  width: fit-content;
  animation-delay: 0.1s;
}

.hero__title {
  font-size: clamp(2.5rem, 5vw, 3.5rem);
  line-height: 1.1;
  animation-delay: 0.2s;
}

.hero__description {
  font-size: 1.2rem;
  max-width: 500px;
  animation-delay: 0.3s;
}

.hero__actions {
  display: flex;
  gap: var(--space-md);
  flex-wrap: wrap;
  animation-delay: 0.4s;
}

.hero__visual {
  display: flex;
  justify-content: center;
  align-items: center;
}

.hero__image-container {
  position: relative;
  width: 350px;
  height: 350px;
  background: linear-gradient(135deg, rgba(232, 141, 154, 0.2), rgba(181, 168, 212, 0.2));
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.hero__character {
  font-size: 8rem;
  filter: drop-shadow(0 10px 20px rgba(0,0,0,0.1));
}

.hero__yarn {
  position: absolute;
  font-size: 2.5rem;
  animation: float 3s ease-in-out infinite;
}

.hero__yarn--1 {
  top: 20px;
  left: 20px;
  animation-delay: 0s;
}

.hero__yarn--2 {
  top: 50px;
  right: 30px;
  animation-delay: 0.5s;
}

.hero__yarn--3 {
  bottom: 40px;
  right: 50px;
  animation-delay: 1s;
}

@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-15px); }
}

@media (max-width: 968px) {
  .hero__container {
    grid-template-columns: 1fr;
    text-align: center;
  }

  .hero__content {
    align-items: center;
  }

  .hero__description {
    max-width: 100%;
  }

  .hero__visual {
    order: -1;
  }

  .hero__image-container {
    width: 280px;
    height: 280px;
  }

  .hero__character {
    font-size: 6rem;
  }
}
</style>
