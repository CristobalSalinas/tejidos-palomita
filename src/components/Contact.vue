<script setup lang="ts">
import { ref } from 'vue'

const form = ref({
  name: '',
  email: '',
  message: '',
})

const isSubmitting = ref(false)
const submitted = ref(false)

const socialLinks = [
  { name: 'Instagram', icon: '📸', url: '#' },
  { name: 'Facebook', icon: '👍', url: '#' },
  { name: 'WhatsApp', icon: '💬', url: '#' },
]

const handleSubmit = () => {
  isSubmitting.value = true
  // Simular envío
  setTimeout(() => {
    isSubmitting.value = false
    submitted.value = true
    form.value = { name: '', email: '', message: '' }
  }, 1500)
}
</script>

<template>
  <section id="contacto" class="contact section">
    <div class="container">
      <div class="contact__grid">
        <div class="contact__info">
          <span class="contact__badge">Contacto</span>
          <h2 class="contact__title">
            ¿Tienes un personaje en mente? <span class="text-gradient">¡Hablemos!</span>
          </h2>
          <p class="contact__description">
            Cuéntame sobre el personaje que te gustaría tener en amigurumi. 
            Estaré encantada de ayudarte a hacerlo realidad.
          </p>

          <div class="contact__social">
            <p class="contact__social-title">Sígueme en redes:</p>
            <div class="contact__social-links">
              <a
                v-for="link in socialLinks"
                :key="link.name"
                :href="link.url"
                class="contact__social-link"
                :title="link.name"
              >
                <span>{{ link.icon }}</span>
                <span>{{ link.name }}</span>
              </a>
            </div>
          </div>
        </div>

        <form class="contact__form card" @submit.prevent="handleSubmit">
          <div v-if="!submitted">
            <div class="contact__form-group">
              <label for="name">Nombre</label>
              <input
                id="name"
                v-model="form.name"
                type="text"
                placeholder="Tu nombre"
                required
              />
            </div>

            <div class="contact__form-group">
              <label for="email">Email</label>
              <input
                id="email"
                v-model="form.email"
                type="email"
                placeholder="tu@email.com"
                required
              />
            </div>

            <div class="contact__form-group">
              <label for="message">Mensaje</label>
              <textarea
                id="message"
                v-model="form.message"
                placeholder="Cuéntame sobre el personaje que deseas..."
                required
              ></textarea>
            </div>

            <button type="submit" class="btn btn-primary contact__submit" :disabled="isSubmitting">
              <span v-if="!isSubmitting">Enviar Mensaje</span>
              <span v-else>Enviando...</span>
            </button>
          </div>

          <div v-else class="contact__success">
            <span class="contact__success-icon">✨</span>
            <h3>¡Mensaje enviado!</h3>
            <p>Gracias por contactarme. Te responderé pronto.</p>
          </div>
        </form>
      </div>
    </div>
  </section>
</template>

<style scoped>
.contact {
  background: var(--bg-cream);
}

.contact__grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--space-3xl);
  align-items: start;
}

.contact__info {
  display: flex;
  flex-direction: column;
  gap: var(--space-lg);
}

.contact__badge {
  font-family: var(--font-heading);
  font-size: 0.9rem;
  font-weight: 600;
  color: var(--color-primary);
  text-transform: uppercase;
  letter-spacing: 1px;
}

.contact__title {
  font-size: clamp(1.8rem, 4vw, 2.5rem);
  line-height: 1.2;
}

.contact__description {
  font-size: 1.1rem;
  line-height: 1.7;
}

.contact__social {
  margin-top: var(--space-lg);
}

.contact__social-title {
  font-weight: 600;
  color: var(--text-dark);
  margin-bottom: var(--space-md);
}

.contact__social-links {
  display: flex;
  gap: var(--space-md);
  flex-wrap: wrap;
}

.contact__social-link {
  display: flex;
  align-items: center;
  gap: var(--space-sm);
  padding: var(--space-sm) var(--space-md);
  background: white;
  border-radius: var(--radius-full);
  font-weight: 600;
  color: var(--text-dark);
  text-decoration: none;
  transition: all var(--transition-base);
  box-shadow: var(--shadow-sm);
}

.contact__social-link:hover {
  transform: translateY(-2px);
  box-shadow: var(--shadow-md);
  color: var(--color-primary);
}

.contact__form {
  padding: var(--space-xl);
}

.contact__form-group {
  margin-bottom: var(--space-lg);
}

.contact__submit {
  width: 100%;
  padding: var(--space-md) var(--space-xl);
}

.contact__submit:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

.contact__success {
  text-align: center;
  padding: var(--space-xl);
}

.contact__success-icon {
  font-size: 4rem;
  display: block;
  margin-bottom: var(--space-md);
}

.contact__success h3 {
  color: var(--color-primary);
  margin-bottom: var(--space-sm);
}

@media (max-width: 968px) {
  .contact__grid {
    grid-template-columns: 1fr;
  }

  .contact__info {
    text-align: center;
    align-items: center;
  }

  .contact__social-links {
    justify-content: center;
  }
}
</style>
