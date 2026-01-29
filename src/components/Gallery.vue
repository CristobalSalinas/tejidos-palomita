<script setup lang="ts">
import { ref, computed } from 'vue'

interface GalleryItem {
  id: number
  title: string
  category: 'videojuegos' | 'anime' | 'series'
  emoji: string
  description: string
}

const activeFilter = ref<string>('todos')

const filters = [
  { id: 'todos', label: 'Todos', icon: '✨' },
  { id: 'videojuegos', label: 'Videojuegos', icon: '🎮' },
  { id: 'anime', label: 'Anime', icon: '🌸' },
  { id: 'series', label: 'Series', icon: '📺' },
]

const galleryItems: GalleryItem[] = [
  { id: 1, title: 'Pikachu', category: 'videojuegos', emoji: '⚡', description: 'El pokémon más querido' },
  { id: 2, title: 'Kirby', category: 'videojuegos', emoji: '🩷', description: 'La bolita rosa adorable' },
  { id: 3, title: 'Totoro', category: 'anime', emoji: '🌿', description: 'El espíritu del bosque' },
  { id: 4, title: 'Naruto', category: 'anime', emoji: '🍥', description: 'El ninja más determinado' },
  { id: 5, title: 'Baby Yoda', category: 'series', emoji: '💚', description: 'El niño más tierno' },
  { id: 6, title: 'Stitch', category: 'series', emoji: '💙', description: 'Experimento 626' },
  { id: 7, title: 'Mario', category: 'videojuegos', emoji: '🍄', description: 'El fontanero legendario' },
  { id: 8, title: 'Sailor Moon', category: 'anime', emoji: '🌙', description: 'La guerrera lunar' },
  { id: 9, title: 'Among Us', category: 'videojuegos', emoji: '🚀', description: 'Tripulante espacial' },
]

const filteredItems = computed(() => {
  if (activeFilter.value === 'todos') return galleryItems
  return galleryItems.filter(item => item.category === activeFilter.value)
})

const setFilter = (filterId: string) => {
  activeFilter.value = filterId
}
</script>

<template>
  <section id="galeria" class="gallery section">
    <div class="container">
      <div class="section-title">
        <h2>Mi <span class="text-gradient">Galería</span></h2>
        <p>Explora mis creaciones más recientes, cada una tejida con dedicación y amor por los detalles.</p>
      </div>

      <div class="gallery__filters">
        <button
          v-for="filter in filters"
          :key="filter.id"
          class="gallery__filter-btn"
          :class="{ 'gallery__filter-btn--active': activeFilter === filter.id }"
          @click="setFilter(filter.id)"
        >
          <span>{{ filter.icon }}</span>
          <span>{{ filter.label }}</span>
        </button>
      </div>

      <div class="gallery__grid">
        <article
          v-for="item in filteredItems"
          :key="item.id"
          class="gallery__card card"
        >
          <div class="gallery__card-image">
            <span class="gallery__card-emoji">{{ item.emoji }}</span>
          </div>
          <div class="gallery__card-content">
            <span class="gallery__card-category">{{ item.category }}</span>
            <h3 class="gallery__card-title">{{ item.title }}</h3>
            <p class="gallery__card-description">{{ item.description }}</p>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<style scoped>
.gallery {
  background: var(--bg-cream);
}

.gallery__filters {
  display: flex;
  justify-content: center;
  gap: var(--space-md);
  flex-wrap: wrap;
  margin-bottom: var(--space-2xl);
}

.gallery__filter-btn {
  display: flex;
  align-items: center;
  gap: var(--space-sm);
  padding: var(--space-sm) var(--space-lg);
  font-family: var(--font-heading);
  font-size: 0.95rem;
  font-weight: 600;
  background: white;
  border: 2px solid transparent;
  border-radius: var(--radius-full);
  cursor: pointer;
  transition: all var(--transition-base);
  color: var(--text-muted);
}

.gallery__filter-btn:hover {
  border-color: var(--color-primary);
  color: var(--color-primary);
}

.gallery__filter-btn--active {
  background: linear-gradient(135deg, var(--color-primary), var(--color-secondary));
  color: white;
  border-color: transparent;
}

.gallery__grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: var(--space-xl);
}

.gallery__card {
  cursor: pointer;
}

.gallery__card-image {
  height: 200px;
  background: linear-gradient(135deg, rgba(232, 141, 154, 0.1), rgba(181, 168, 212, 0.1));
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background var(--transition-base);
}

.gallery__card:hover .gallery__card-image {
  background: linear-gradient(135deg, rgba(232, 141, 154, 0.2), rgba(181, 168, 212, 0.2));
}

.gallery__card-emoji {
  font-size: 5rem;
  transition: transform var(--transition-base);
}

.gallery__card:hover .gallery__card-emoji {
  transform: scale(1.1);
}

.gallery__card-content {
  padding: var(--space-lg);
}

.gallery__card-category {
  display: inline-block;
  font-size: 0.75rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  color: var(--color-primary);
  background: rgba(232, 141, 154, 0.1);
  padding: var(--space-xs) var(--space-sm);
  border-radius: var(--radius-sm);
  margin-bottom: var(--space-sm);
}

.gallery__card-title {
  font-size: 1.25rem;
  margin-bottom: var(--space-sm);
}

.gallery__card-description {
  font-size: 0.95rem;
  margin: 0;
}

@media (max-width: 768px) {
  .gallery__grid {
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: var(--space-lg);
  }
}
</style>
