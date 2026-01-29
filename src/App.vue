<script setup lang="ts">
import Header from './components/Header.vue'
import Hero from './components/Hero.vue'
import Gallery from './components/Gallery.vue'
import About from './components/About.vue'
import Categories from './components/Categories.vue'
import Contact from './components/Contact.vue'
import Footer from './components/Footer.vue'
</script>

<template>
  <div class="app">
    <Header />
    <main>
      <Hero />
      <Categories />
      <Gallery />
      <About />
      <Contact />
    </main>
    <Footer />
  </div>
</template>

<style scoped>
.app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

main {
  flex: 1;
}
</style>
