<template>
  <div>
    <Header 
      logo="ShopVibe"
      :navigation-items="navItems"
      :cta-button="{ text: 'Shop Now', href: '#products' }"
    />
    <Hero 
      title="Discover Amazing Products at Unbeatable Prices"
      subtitle="Shop the latest trends in fashion, electronics, and lifestyle products with free shipping on orders over $50."
      :buttons="heroButtons"
      background-color="linear-gradient(135deg, #ff6b6b 0%, #ee5a24 100%)"
    />
    <Footer 
      brand-name="ShopVibe"
      description="Your one-stop shop for quality products at amazing prices. Fast shipping, easy returns, and excellent customer service."
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
  { label: 'Categories', href: '#categories' },
  { label: 'New Arrivals', href: '#new-arrivals' },
  { label: 'Sale', href: '#sale' },
  { label: 'About', href: '#about' },
  { label: 'Contact', href: '#contact' }
]

const heroButtons = [
  { text: 'Shop Collection', variant: 'primary', action: 'scroll', target: '#products' },
  { text: 'View Deals', variant: 'secondary', action: 'scroll', target: '#sale' }
]

const socialLinks = [
  { platform: 'Facebook', url: 'https://facebook.com' },
  { platform: 'Instagram', url: 'https://instagram.com' },
  { platform: 'Twitter', url: 'https://twitter.com' },
  { platform: 'Pinterest', url: 'https://pinterest.com' },
  { platform: 'YouTube', url: 'https://youtube.com' }
]

const footerSections = [
  {
    title: 'Shop',
    links: [
      { text: 'All Products', href: '#products' },
      { text: 'Fashion', href: '#fashion' },
      { text: 'Electronics', href: '#electronics' },
      { text: 'Home & Garden', href: '#home-garden' },
      { text: 'Sports & Outdoors', href: '#sports' }
    ]
  },
  {
    title: 'Customer Service',
    links: [
      { text: 'Contact Us', href: '#contact' },
      { text: 'Shipping Info', href: '#shipping' },
      { text: 'Returns & Exchanges', href: '#returns' },
      { text: 'Size Guide', href: '#size-guide' },
      { text: 'FAQ', href: '#faq' }
    ]
  },
  {
    title: 'Account',
    links: [
      { text: 'My Account', href: '#account' },
      { text: 'Order History', href: '#orders' },
      { text: 'Wishlist', href: '#wishlist' },
      { text: 'Track Order', href: '#track' },
      { text: 'Rewards Program', href: '#rewards' }
    ]
  }
]
</script>

<style scoped>
/* Ecommerce-specific styles can go here */
</style>

