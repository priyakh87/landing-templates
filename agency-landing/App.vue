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
    
    <!-- Portfolio Section with NPM Drag & Drop Widget -->
    <section id="portfolio" class="portfolio-section">
      <DragDropWidget
        title="Our Featured Portfolio"
        subtitle="Drag and drop to explore our projects by your interests"
        :items="portfolioItems"
        layout="grid"
        :show-controls="true"
        :show-add-button="false"
        :editable="true"
        @item-action="handlePortfolioAction"
        @items-reordered="handlePortfolioReorder"
      />
    </section>
    
    <!-- Team Section -->
    <section id="team" class="team-section">
      <DragDropWidget
        title="Meet Our Creative Team"
        subtitle="Get to know the talented individuals behind our success"
        :items="teamMembers"
        layout="grid"
        :show-controls="false"
        :show-add-button="false"
        :editable="true"
        @item-action="handleTeamAction"
        @items-reordered="handleTeamReorder"
      />
    </section>
    
    <!-- Services Section -->
    <section id="services" class="services-section">
      <DragDropWidget
        title="Our Creative Services"
        subtitle="Arrange services by your priority to see what matters most to your project"
        :items="agencyServices"
        layout="list"
        :show-controls="true"
        :show-add-button="false"
        :editable="true"
        @item-action="handleServiceAction"
        @items-reordered="handleServicesReorder"
      />
    </section>
    
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

// Method 5: Direct component import (most likely to work)
import DragDropWidget from 'vue-drag-drop-widget/src/DragDropWidget.vue';

import { ref } from 'vue';

const navItems = [
  { label: 'Home', href: '#home' },
  { label: 'Portfolio', href: '#portfolio' },
  { label: 'Services', href: '#services' },
  { label: 'Team', href: '#team' },
  { label: 'About', href: '#about' },
  { label: 'Contact', href: '#contact' }
]

const heroButtons = [
  { text: 'View Portfolio', variant: 'primary', action: 'scroll', target: '#portfolio' },
  { text: 'Get Quote', variant: 'secondary', action: 'scroll', target: '#contact' }
]

// Portfolio items with agency work
const portfolioItems = ref([
  {
    id: 1,
    title: 'TechFlow - SaaS Platform Redesign',
    image: 'https://images.unsplash.com/photo-1460925895917-afdab827c52f?w=500&h=300&fit=crop',
    description: 'Complete UI/UX overhaul for a B2B SaaS platform, resulting in 45% increase in user engagement and 30% boost in conversions.',
    tags: ['Web Design', 'UI/UX', 'SaaS'],
    button: {
      text: 'View Case Study',
      variant: 'primary',
      action: 'external',
      href: 'https://example.com/case-study-techflow'
    }
  },
  {
    id: 2,
    title: 'GreenLeaf - E-commerce Brand Identity',
    image: 'https://images.unsplash.com/photo-1558618666-fcd25c85cd64?w=500&h=300&fit=crop',
    description: 'Sustainable brand identity design for eco-friendly e-commerce startup, including logo, packaging, and digital presence.',
    tags: ['Branding', 'E-commerce', 'Sustainability'],
    button: {
      text: 'Explore Brand',
      variant: 'primary',
      action: 'external',
      href: 'https://example.com/greenleaf-brand'
    }
  },
  {
    id: 3,
    title: 'HealthTech Mobile App',
    image: 'https://images.unsplash.com/photo-1512941937669-90a1b58e7e9c?w=500&h=300&fit=crop',
    description: 'User-centered mobile app design for healthcare technology startup, now serving 100K+ patients worldwide.',
    tags: ['Mobile Design', 'Healthcare', 'UX Research'],
    button: {
      text: 'See App Design',
      variant: 'primary',
      action: 'external',
      href: 'https://example.com/healthtech-app'
    }
  },
  {
    id: 4,
    title: 'RetailMax - Omnichannel Experience',
    image: 'https://images.unsplash.com/photo-1556742049-0cfed4f6a45d?w=500&h=300&fit=crop',
    description: 'Integrated retail experience design across digital and physical touchpoints for major retail chain.',
    tags: ['Retail Design', 'Omnichannel', 'Customer Experience'],
    button: {
      text: 'View Project',
      variant: 'primary',
      action: 'external',
      href: 'https://example.com/retailmax'
    }
  },
  {
    id: 5,
    title: 'FinanceFlow - Banking Dashboard',
    image: 'https://images.unsplash.com/photo-1551288049-bebda4e38f71?w=500&h=300&fit=crop',
    description: 'Enterprise banking dashboard design with advanced data visualization and intuitive user workflows.',
    tags: ['Fintech', 'Dashboard Design', 'Data Visualization'],
    button: {
      text: 'Case Study',
      variant: 'primary',
      action: 'external',
      href: 'https://example.com/financeflow'
    }
  },
  {
    id: 6,
    title: 'EduTech Learning Platform',
    image: 'https://images.unsplash.com/photo-1501504905252-473c47e087f8?w=500&h=300&fit=crop',
    description: 'Interactive learning platform design for online education, supporting 50K+ students globally.',
    tags: ['EdTech', 'E-learning', 'Interactive Design'],
    button: {
      text: 'Explore Platform',
      variant: 'primary',
      action: 'external',
      href: 'https://example.com/edutech'
    }
  }
])

// Team members
const teamMembers = ref([
  {
    id: 1,
    title: 'Sarah Chen - Creative Director',
    image: 'https://images.unsplash.com/photo-1494790108755-2616b612b647?w=400&h=400&fit=crop&crop=face',
    description: '10+ years in creative direction with expertise in brand strategy and visual identity. Former Apple design team member.',
    tags: ['Creative Direction', 'Brand Strategy', 'Visual Identity'],
    button: {
      text: 'View Profile',
      variant: 'primary',
      action: 'external',
      href: '#sarah-profile'
    }
  },
  {
    id: 2,
    title: 'Marcus Rodriguez - Lead Developer',
    image: 'https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?w=400&h=400&fit=crop&crop=face',
    description: 'Full-stack developer specializing in React, Vue.js, and modern web technologies. Built 50+ web applications.',
    tags: ['Frontend Development', 'React', 'Vue.js'],
    button: {
      text: 'See Work',
      variant: 'primary',
      action: 'external',
      href: '#marcus-portfolio'
    }
  },
  {
    id: 3,
    title: 'Emily Johnson - UX Designer',
    image: 'https://images.unsplash.com/photo-1438761681033-6461ffad8d80?w=400&h=400&fit=crop&crop=face',
    description: 'User experience specialist with psychology background. Conducts user research and creates intuitive designs.',
    tags: ['UX Design', 'User Research', 'Prototyping'],
    button: {
      text: 'Contact Emily',
      variant: 'primary',
      action: 'external',
      href: '#emily-contact'
    }
  },
  {
    id: 4,
    title: 'David Kim - Brand Strategist',
    image: 'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=400&h=400&fit=crop&crop=face',
    description: 'Strategic brand consultant helping startups and enterprises build compelling brand narratives and market positioning.',
    tags: ['Brand Strategy', 'Marketing', 'Consulting'],
    button: {
      text: 'Learn More',
      variant: 'primary',
      action: 'external',
      href: '#david-strategy'
    }
  }
])

// Agency services
const agencyServices = ref([
  {
    id: 1,
    title: 'Brand Strategy & Identity Design',
    image: 'https://images.unsplash.com/photo-1558655146-d09347e92766?w=500&h=300&fit=crop',
    description: 'Comprehensive brand development from strategy to visual identity. We help define your brand personality, positioning, and create memorable visual systems.',
    tags: ['Brand Strategy', 'Logo Design', 'Visual Identity'],
    button: {
      text: 'Start Branding Project',
      variant: 'primary',
      action: 'scroll',
      target: '#contact'
    }
  },
  {
    id: 2,
    title: 'Web Design & Development',
    image: 'https://images.unsplash.com/photo-1547658719-da2b51169166?w=500&h=300&fit=crop',
    description: 'Custom website design and development with focus on user experience, performance, and conversion optimization.',
    tags: ['Web Design', 'Frontend Development', 'UX/UI'],
    button: {
      text: 'Get Website Quote',
      variant: 'primary',
      action: 'scroll',
      target: '#contact'
    }
  },
  {
    id: 3,
    title: 'Digital Marketing & Growth',
    image: 'https://images.unsplash.com/photo-1432888498266-38ffec3eaf0a?w=500&h=300&fit=crop',
    description: 'Data-driven digital marketing strategies including social media, content marketing, SEO, and paid advertising campaigns.',
    tags: ['Digital Marketing', 'SEO', 'Social Media'],
    button: {
      text: 'Discuss Marketing',
      variant: 'primary',
      action: 'scroll',
      target: '#contact'
    }
  }
])

const socialLinks = [
  { platform: 'Behance', url: 'https://behance.net/creativehub' },
  { platform: 'Dribbble', url: 'https://dribbble.com/creativehub' },
  { platform: 'Instagram', url: 'https://instagram.com/creativehub' },
  { platform: 'LinkedIn', url: 'https://linkedin.com/company/creativehub' }
]

const footerSections = [
  {
    title: 'Services',
    links: [
      { text: 'Brand Design', href: '#branding' },
      { text: 'Web Development', href: '#web-dev' },
      { text: 'Digital Marketing', href: '#marketing' },
      { text: 'UI/UX Design', href: '#ui-ux' }
    ]
  },
  {
    title: 'Company',
    links: [
      { text: 'About Us', href: '#about' },
      { text: 'Our Process', href: '#process' },
      { text: 'Case Studies', href: '#cases' },
      { text: 'Careers', href: '#careers' }
    ]
  }
]

// Event handlers
const handlePortfolioAction = (item) => {
  console.log('Portfolio item clicked:', item.title)
  
  if (item.button?.action === 'external' && item.button?.href) {
    window.open(item.button.href, '_blank')
  }
}

const handlePortfolioReorder = (reorderedItems) => {
  console.log('Portfolio reordered:', reorderedItems.map(item => item.title))
  localStorage.setItem('agencyPortfolioOrder', JSON.stringify(reorderedItems))
}

const handleTeamAction = (member) => {
  console.log('Team member clicked:', member.title)
  
  if (member.button?.href) {
    console.log(`Opening profile for: ${member.title}`)
  }
}

const handleTeamReorder = (reorderedMembers) => {
  console.log('Team members reordered:', reorderedMembers.map(member => member.title))
  localStorage.setItem('agencyTeamOrder', JSON.stringify(reorderedMembers))
}

const handleServiceAction = (service) => {
  console.log('Service action clicked:', service.title)
}

const handleServicesReorder = (reorderedServices) => {
  console.log('Services reordered by priority:', reorderedServices.map(service => service.title))
  localStorage.setItem('agencyServicesOrder', JSON.stringify(reorderedServices))
}
</script>

<style scoped>
.portfolio-section {
  padding: 4rem 0;
  background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
}

.team-section {
  padding: 4rem 0;
  background: #ffffff;
}

.services-section {
  padding: 4rem 0;
  background: #f8f9fa;
}

/* Agency-specific styling overrides for the npm package */
:deep(.drag-drop-widget) {
  font-family: 'Helvetica Neue', Arial, sans-serif;
}

:deep(.widget-title) {
  color: #2c3e50;
  font-weight: 700;
  font-size: 2.8rem;
}

:deep(.widget-subtitle) {
  color: #5a6c7d;
  font-size: 1.2rem;
}

:deep(.tag) {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  font-weight: 500;
}

:deep(.item-button.primary) {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border: none;
  font-weight: 600;
  transition: all 0.3s ease;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

:deep(.item-button.primary:hover) {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(102, 126, 234, 0.4);
}

:deep(.drag-item) {
  border: 1px solid #e9ecef;
  transition: all 0.4s ease;
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
}

:deep(.drag-item:hover) {
  border-color: #667eea;
  box-shadow: 0 12px 35px rgba(102, 126, 234, 0.2);
  transform: translateY(-5px);
}

:deep(.item-title) {
  color: #2c3e50;
  font-weight: 600;
  font-size: 1.3rem;
}

:deep(.item-description) {
  color: #6c757d;
  line-height: 1.6;
}

/* Team section specific styling */
.team-section :deep(.drag-item) {
  text-align: center;
}

.team-section :deep(.item-image) {
  border-radius: 50%;
  overflow: hidden;
  width: 150px;
  height: 150px;
  margin: 0 auto 1rem;
}

.team-section :deep(.item-image img) {
  border-radius: 50%;
}

/* Services section specific styling */
.services-section :deep(.drag-container.list-layout) {
  max-width: 800px;
  margin: 0 auto;
}

.services-section :deep(.list-layout .drag-item) {
  margin-bottom: 1.5rem;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .portfolio-section,
  .team-section,
  .services-section {
    padding: 2rem 0;
  }
  
  :deep(.widget-title) {
    font-size: 2.2rem;
  }
  
  .team-section :deep(.item-image) {
    width: 120px;
    height: 120px;
  }
}
</style>

