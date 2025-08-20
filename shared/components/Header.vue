<template>
  <header class="header">
    <nav class="navbar">
      <div class="nav-container">
        <div class="nav-logo">
          <a href="/" class="nav-logo-link">
            {{ logo || 'Brand' }}
          </a>
        </div>
        
        <div class="nav-menu" :class="{ 'active': isMenuOpen }">
          <a 
            v-for="item in navigationItems" 
            :key="item.label"
            :href="item.href" 
            class="nav-link"
            @click="closeMenu"
          >
            {{ item.label }}
          </a>
          <button v-if="ctaButton" class="nav-cta-btn">
            {{ ctaButton.text }}
          </button>
        </div>
        
        <div class="nav-toggle" @click="toggleMenu">
          <span class="bar"></span>
          <span class="bar"></span>
          <span class="bar"></span>
        </div>
      </div>
    </nav>
  </header>
</template>

<script setup>
import { ref } from 'vue'

const props = defineProps({
  logo: {
    type: String,
    default: 'Brand'
  },
  navigationItems: {
    type: Array,
    default: () => [
      { label: 'Home', href: '#home' },
      { label: 'About', href: '#about' },
      { label: 'Services', href: '#services' },
      { label: 'Contact', href: '#contact' }
    ]
  },
  ctaButton: {
    type: Object,
    default: () => ({ text: 'Get Started', href: '#contact' })
  }
})

const isMenuOpen = ref(false)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const closeMenu = () => {
  isMenuOpen.value = false
}
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
  width: 100%;
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  z-index: 1000;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.navbar {
  padding: 1rem 0;
}

.nav-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.nav-logo-link {
  font-size: 1.5rem;
  font-weight: bold;
  text-decoration: none;
  color: #333;
}

.nav-menu {
  display: flex;
  align-items: center;
  gap: 2rem;
}

.nav-link {
  text-decoration: none;
  color: #666;
  font-weight: 500;
  transition: color 0.3s ease;
}

.nav-link:hover {
  color: #007bff;
}

.nav-cta-btn {
  background: #007bff;
  color: white;
  border: none;
  padding: 0.75rem 1.5rem;
  border-radius: 25px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.3s ease;
}

.nav-cta-btn:hover {
  background: #0056b3;
}

.nav-toggle {
  display: none;
  flex-direction: column;
  cursor: pointer;
}

.bar {
  width: 25px;
  height: 3px;
  background: #333;
  margin: 3px 0;
  transition: 0.3s;
}

@media (max-width: 768px) {
  .nav-menu {
    position: fixed;
    left: -100%;
    top: 70px;
    flex-direction: column;
    background: white;
    width: 100%;
    text-align: center;
    transition: 0.3s;
    box-shadow: 0 10px 27px rgba(0, 0, 0, 0.05);
    padding: 2rem 0;
  }

  .nav-menu.active {
    left: 0;
  }

  .nav-toggle {
    display: flex;
  }
}
</style>

