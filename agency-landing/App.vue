<template>
  <div>
    <Header 
      logo="CreativeHub"
      :navigation-items="navItems"
      :cta-button="{ text: 'Start Project', href: '#contact' }"
    />
    <Hero 
      title="Award-Winning Creative Agency"
      subtitle="We craft exceptional digital experiences that drive results for ambitious brands worldwide."
      :buttons="heroButtons"
      background-color="linear-gradient(135deg, #667eea 0%, #764ba2 100%)"
    />
    <Footer 
      brand-name="CreativeHub"
      description="A full-service creative agency specializing in branding, web design, and digital marketing."
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
  { label: 'Services', href: '#services' },
  { label: 'Portfolio', href: '#portfolio' },
  { label: 'About', href: '#about' },
  { label: 'Blog', href: '#blog' },
  { label: 'Contact', href: '#contact' }
]

const heroButtons = [
  { text: 'View Our Work', variant: 'primary', action: 'scroll', target: '#portfolio' },
  { text: 'Get Quote', variant: 'secondary', action: 'scroll', target: '#contact' }
]

const socialLinks = [
  { platform: 'Behance', url: 'https://behance.net' },
  { platform: 'Dribbble', url: 'https://dribbble.com' },
  { platform: 'Instagram', url: 'https://instagram.com' },
  { platform: 'LinkedIn', url: 'https://linkedin.com' },
  { platform: 'Twitter', url: 'https://twitter.com' }
]

const footerSections = [
  {
    title: 'Services',
    links: [
      { text: 'Branding & Identity', href: '#branding' },
      { text: 'Web Design', href: '#web-design' },
      { text: 'Digital Marketing', href: '#marketing' },
      { text: 'UI/UX Design', href: '#ui-ux' },
      { text: 'Development', href: '#development' }
    ]
  },
  {
    title: 'Company',
    links: [
      { text: 'About Us', href: '#about' },
      { text: 'Our Team', href: '#team' },
      { text: 'Careers', href: '#careers' },
      { text: 'Case Studies', href: '#case-studies' }
    ]
  },
  {
    title: 'Resources',
    links: [
      { text: 'Blog', href: '#blog' },
      { text: 'Design Tools', href: '#tools' },
      { text: 'Free Resources', href: '#resources' },
      { text: 'Newsletter', href: '#newsletter' }
    ]
  }
]
</script>

<style scoped>
/* Agency-specific styles can go here */
</style>

