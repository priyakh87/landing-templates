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

const navItems = [
  { label: 'Home', href: '#home' },
  { label: 'About', href: '#about' },
  { label: 'Services', href: '#services' },
  { label: 'Testimonials', href: '#testimonials' },
  { label: 'Contact', href: '#contact' }
]

const heroButtons = [
  { text: 'Start Your Journey', variant: 'primary', action: 'scroll', target: '#contact' },
  { text: 'Learn More', variant: 'secondary', action: 'scroll', target: '#about' }
]

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
</script>

