<template>
  <section class="hero" :class="theme" :style="heroStyles">
    <div class="hero-container">
      <div class="hero-content" :class="{ 'reverse': reverse }">
        <div class="hero-text">
          <h1 class="hero-title">{{ title }}</h1>
          <p class="hero-subtitle">{{ subtitle }}</p>
          <div class="hero-buttons">
            <button 
              v-for="button in buttons" 
              :key="button.text"
              :class="['btn', button.variant || 'primary']"
              @click="handleButtonClick(button)"
            >
              {{ button.text }}
            </button>
          </div>
        </div>
        <div v-if="image" class="hero-image">
          <img :src="image" :alt="imageAlt" />
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  title: {
    type: String,
    default: 'Transform Your Life Today'
  },
  subtitle: {
    type: String,
    default: 'Join thousands of people who have already started their journey to success.'
  },
  buttons: {
    type: Array,
    default: () => [
      { text: 'Get Started', variant: 'primary', action: 'scroll', target: '#contact' },
      { text: 'Learn More', variant: 'secondary', action: 'scroll', target: '#about' }
    ]
  },
  image: {
    type: String,
    default: null
  },
  imageAlt: {
    type: String,
    default: 'Hero image'
  },
  backgroundColor: {
    type: String,
    default: 'linear-gradient(135deg, #667eea 0%, #764ba2 100%)'
  },
  theme: {
    type: String,
    default: 'default',
    validator: value => ['default', 'agency', 'ecommerce', 'coach'].includes(value)
  },
  reverse: {
    type: Boolean,
    default: false
  }
})

const heroStyles = computed(() => ({
  background: props.backgroundColor
}))

const handleButtonClick = (button) => {
  if (button.action === 'scroll' && button.target) {
    document.querySelector(button.target)?.scrollIntoView({ 
      behavior: 'smooth' 
    })
  } else if (button.href) {
    window.open(button.href, button.target || '_self')
  }
}
</script>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  color: white;
  text-align: center;
  padding-top: 80px;
}

.hero-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.hero-content {
  display: grid;
  grid-template-columns: 1fr;
  gap: 4rem;
  align-items: center;
}

.hero-content.reverse {
  grid-template-columns: 1fr 1fr;
}

.hero-content.reverse .hero-text {
  order: 2;
}

.hero-content.reverse .hero-image {
  order: 1;
}

.hero-title {
  font-size: 3.5rem;
  font-weight: bold;
  margin-bottom: 1.5rem;
  line-height: 1.2;
}

.hero-subtitle {
  font-size: 1.25rem;
  margin-bottom: 2rem;
  opacity: 0.9;
  line-height: 1.6;
}

.hero-buttons {
  display: flex;
  gap: 1rem;
  justify-content: center;
}

.btn {
  padding: 1rem 2rem;
  border: none;
  border-radius: 50px;
  font-weight: 600;
  font-size: 1.1rem;
  cursor: pointer;
  transition: all 0.3s ease;
  text-decoration: none;
  display: inline-block;
}

.btn.primary {
  background: white;
  color: #333;
}

.btn.primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
}

.btn.secondary {
  background: transparent;
  color: white;
  border: 2px solid white;
}

.btn.secondary:hover {
  background: white;
  color: #333;
}

.hero-image img {
  max-width: 100%;
  height: auto;
  border-radius: 10px;
}

/* Theme variations */
.hero.agency .hero-title {
  font-family: 'Helvetica Neue', Arial, sans-serif;
  letter-spacing: -0.02em;
}

.hero.ecommerce .btn.primary {
  background: #ff6b6b;
  color: white;
  border: 2px solid #ff6b6b;
}

.hero.ecommerce .btn.primary:hover {
  background: #ee5a24;
  border-color: #ee5a24;
}

.hero.coach .hero-title {
  font-family: Georgia, serif;
}

@media (max-width: 768px) {
  .hero-content {
    grid-template-columns: 1fr;
    text-align: center;
    gap: 2rem;
  }
  
  .hero-content.reverse .hero-text,
  .hero-content.reverse .hero-image {
    order: unset;
  }
  
  .hero-title {
    font-size: 2.5rem;
  }
  
  .hero-buttons {
    flex-direction: column;
    align-items: center;
  }
}
</style>