<script setup lang="ts">
const categories = [
  {
    id: 'videojuegos',
    icon: '🎮',
    title: 'Videojuegos',
    description: 'Personajes icónicos de tus juegos favoritos: Pokémon, Mario, Zelda, Animal Crossing y más.',
    examples: ['Pikachu', 'Kirby', 'Link', 'Mario'],
  },
  {
    id: 'anime',
    icon: '🌸',
    title: 'Anime',
    description: 'Los protagonistas de las series que marcaron tu infancia y las nuevas que te emocionan.',
    examples: ['Totoro', 'Naruto', 'Sailor Moon', 'Goku'],
  },
  {
    id: 'series',
    icon: '📺',
    title: 'Series & Películas',
    description: 'Characters de tus series y películas favoritas de Disney, Marvel, Star Wars y más.',
    examples: ['Baby Yoda', 'Stitch', 'Minions', 'Hulk'],
  },
]
</script>

<template>
  <section class="categories section">
    <div class="container">
      <div class="section-title">
        <h2>¿Qué puedo <span class="text-gradient">crear para ti</span>?</h2>
        <p>Especializada en crear amigurumis de personajes de diferentes universos</p>
      </div>

      <div class="categories__grid">
        <article
          v-for="category in categories"
          :key="category.id"
          class="categories__card card"
        >
          <div class="categories__icon">{{ category.icon }}</div>
          <h3 class="categories__title">{{ category.title }}</h3>
          <p class="categories__description">{{ category.description }}</p>
          <div class="categories__examples">
            <span
              v-for="example in category.examples"
              :key="example"
              class="categories__tag"
            >
              {{ example }}
            </span>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<style scoped>
.categories {
  background: linear-gradient(180deg, var(--bg-light) 0%, var(--bg-cream) 100%);
}

.categories__grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: var(--space-xl);
}

.categories__card {
  padding: var(--space-xl);
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: var(--space-md);
}

.categories__icon {
  font-size: 4rem;
  margin-bottom: var(--space-sm);
}

.categories__title {
  font-size: 1.5rem;
  color: var(--text-dark);
}

.categories__description {
  font-size: 1rem;
  line-height: 1.6;
  max-width: 280px;
}

.categories__examples {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: var(--space-sm);
  margin-top: var(--space-sm);
}

.categories__tag {
  font-size: 0.8rem;
  font-weight: 600;
  padding: var(--space-xs) var(--space-sm);
  background: rgba(232, 141, 154, 0.1);
  color: var(--color-primary);
  border-radius: var(--radius-sm);
}
</style>
