<template>
  <div>
    <Header 
      logo="CoachPro"
      :navigation-items="navItems"
      :cta-button="{ text: 'Book Session', href: '#contact' }"
    />
    <Hero 
      title="Transform Your Life with Professional Coaching"
      subtitle="Unlock your potential and achieve your goals with personalized coaching sessions."
      :buttons="heroButtons"
      background-color="linear-gradient(135deg, #667eea 0%, #764ba2 100%)"
    />
    
    <!-- Services Section with Drag & Drop Widget -->
    <section id="services" class="services-section">
      <DragDropWidget
        title="Our Coaching Services"
        subtitle="Drag and drop to reorder our services based on your interests"
        :items="coachingServices"
        layout="grid"
        @item-action="handleServiceAction"
        @items-reordered="handleServicesReorder"
      />
    </section>
    
    <Footer 
      brand-name="CoachPro"
      description="Empowering individuals to reach their full potential through professional coaching."
      :social-links="socialLinks"
      :footer-sections="footerSections"
    />
  </div>
</template>

<script setup>
import Header from '@shared/components/Header.vue';
import Hero from '@shared/components/Hero.vue';
import Footer from '@shared/components/Footer.vue';
import { DragDropWidget } from '@shared/widgets';
import { ref } from 'vue';

const navItems = [
  { label: 'Home', href: '#home' },
  { label: 'About', href: '#about' },
  { label: 'Services', href: '#services' },
  { label: 'Testimonials', href: '#testimonials' },
  { label: 'Contact', href: '#contact' }
]

const heroButtons = [
  { text: 'Start Your Journey', variant: 'primary', action: 'scroll', target: '#contact' },
  { text: 'Learn More', variant: 'secondary', action: 'scroll', target: '#services' }
]

const coachingServices = ref([
  {
    id: 1,
    title: 'Life Coaching',
    image: 'https://images.unsplash.com/photo-1573496359142-b8d87734a5a2?w=400',
    description: 'Transform your personal life with guided coaching sessions focused on your goals and aspirations.',
    tags: ['Personal Growth', 'Goal Setting', 'Mindset'],
    button: {
      text: 'Learn More',
      variant: 'primary',
      action: 'scroll',
      target: '#contact'
    }
  },
  {
    id: 2,
    title: 'Career Coaching',
    image: 'https://images.unsplash.com/photo-1560472354-b33ff0c44a43?w=400',
    description: 'Advance your career with strategic planning, skill development, and professional guidance.',
    tags: ['Career Development', 'Leadership', 'Skills'],
    button: {
      text: 'Get Started',
      variant: 'primary',
      action: 'scroll',
      target: '#contact'
    }
  },
  {
    id: 3,
    title: 'Business Coaching',
    image: 'https://images.unsplash.com/photo-1553877522-43269d4ea984?w=400',
    description: 'Scale your business with proven strategies, leadership development, and growth planning.',
    tags: ['Business Growth', 'Strategy', 'Leadership'],
    button: {
      text: 'Book Consultation',
      variant: 'primary',
      action: 'scroll',
      target: '#contact'
    }
  }
])

const socialLinks = [
  { platform: 'Facebook', url: 'https://facebook.com' },
  { platform: 'Instagram', url: 'https://instagram.com' },
  { platform: 'LinkedIn', url: 'https://linkedin.com' }
]

const footerSections = [
  {
    title: 'Services',
    links: [
      { text: 'Life Coaching', href: '#life-coaching' },
      { text: 'Career Coaching', href: '#career-coaching' },
      { text: 'Business Coaching', href: '#business-coaching' }
    ]
  },
  {
    title: 'Resources',
    links: [
      { text: 'Blog', href: '#blog' },
      { text: 'Webinars', href: '#webinars' },
      { text: 'Free Tools', href: '#tools' }
    ]
  }
]

const handleServiceAction = (service) => {
  console.log('Service action clicked:', service)
  // Handle service-specific actions here
}

const handleServicesReorder = (reorderedServices) => {
  console.log('Services reordered:', reorderedServices)
  // Save the new order to localStorage or send to API
  localStorage.setItem('coachingServicesOrder', JSON.stringify(reorderedServices))
}
</script>

<style scoped>
.services-section {
  padding: 4rem 0;
  background: #f8f9fa;
}
</style>

