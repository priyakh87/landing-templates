<template>
  <footer class="footer">
    <div class="footer-container">
      <div class="footer-content">
        <div class="footer-section">
          <h3 class="footer-logo">{{ brandName }}</h3>
          <p class="footer-description">{{ description }}</p>
          <div class="social-links">
            <a 
              v-for="social in socialLinks" 
              :key="social.platform"
              :href="social.url" 
              class="social-link"
              target="_blank"
              rel="noopener noreferrer"
            >
              {{ social.platform }}
            </a>
          </div>
        </div>
        
        <div 
          v-for="section in footerSections" 
          :key="section.title"
          class="footer-section"
        >
          <h4 class="footer-title">{{ section.title }}</h4>
          <ul class="footer-links">
            <li v-for="link in section.links" :key="link.text">
              <a :href="link.href" class="footer-link">{{ link.text }}</a>
            </li>
          </ul>
        </div>
      </div>
      
      <div class="footer-bottom">
        <p>&copy; {{ currentYear }} {{ brandName }}. {{ copyrightText }}</p>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  brandName: {
    type: String,
    default: 'Brand'
  },
  description: {
    type: String,
    default: 'Building amazing experiences for our customers.'
  },
  socialLinks: {
    type: Array,
    default: () => [
      { platform: 'Facebook', url: '#' },
      { platform: 'Twitter', url: '#' },
      { platform: 'Instagram', url: '#' },
      { platform: 'LinkedIn', url: '#' }
    ]
  },
  footerSections: {
    type: Array,
    default: () => [
      {
        title: 'Services',
        links: [
          { text: 'Consulting', href: '#' },
          { text: 'Support', href: '#' },
          { text: 'Training', href: '#' }
        ]
      },
      {
        title: 'Company',
        links: [
          { text: 'About', href: '#' },
          { text: 'Contact', href: '#' },
          { text: 'Careers', href: '#' }
        ]
      }
    ]
  },
  copyrightText: {
    type: String,
    default: 'All rights reserved.'
  }
})

const currentYear = computed(() => new Date().getFullYear())
</script>

<style scoped>
.footer {
  background: #1a1a1a;
  color: white;
  padding: 3rem 0 1rem;
}

.footer-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.footer-content {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr;
  gap: 3rem;
  margin-bottom: 2rem;
}

.footer-section {
  display: flex;
  flex-direction: column;
}

.footer-logo {
  font-size: 1.5rem;
  font-weight: bold;
  margin-bottom: 1rem;
  color: #007bff;
}

.footer-description {
  margin-bottom: 1.5rem;
  opacity: 0.8;
  line-height: 1.6;
}

.social-links {
  display: flex;
  gap: 1rem;
}

.social-link {
  color: #ccc;
  text-decoration: none;
  transition: color 0.3s ease;
}

.social-link:hover {
  color: #007bff;
}

.footer-title {
  font-size: 1.1rem;
  font-weight: 600;
  margin-bottom: 1rem;
}

.footer-links {
  list-style: none;
  padding: 0;
}

.footer-links li {
  margin-bottom: 0.5rem;
}

.footer-link {
  color: #ccc;
  text-decoration: none;
  transition: color 0.3s ease;
}

.footer-link:hover {
  color: #007bff;
}

.footer-bottom {
  border-top: 1px solid #333;
  padding-top: 1rem;
  text-align: center;
  opacity: 0.6;
}

@media (max-width: 768px) {
  .footer-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
  
  .social-links {
    justify-content: center;
  }
}
</style>