<template>
  <div>
    <Header 
      logo="ShopHub"
      :navigation-items="navItems"
      :cta-button="{ text: 'Shop Now', href: '#products' }"
    />
    <Hero 
      title="Discover Amazing Products at Unbeatable Prices"
      subtitle="Shop the latest trends and find everything you need with fast shipping and hassle-free returns."
      :buttons="heroButtons"
      background-color="linear-gradient(135deg, #667eea 0%, #764ba2 100%)"
    />
    
    <!-- Featured Products Section with Drag & Drop Widget -->
    <section id="products" class="products-section">
      <DragDropWidget
        title="Featured Products"
        subtitle="Drag and drop to arrange products by your preferences"
        :items="featuredProducts"
        layout="grid"
        :show-controls="true"
        :show-add-button="false"
        @item-action="handleProductAction"
        @items-reordered="handleProductsReorder"
      />
    </section>
    
    <!-- Categories Section -->
    <section id="categories" class="categories-section">
      <DragDropWidget
        title="Shop by Category"
        subtitle="Explore our product categories - reorder by your shopping interests"
        :items="productCategories"
        layout="grid"
        :show-controls="true"
        :show-add-button="false"
        @item-action="handleCategoryAction"
        @items-reordered="handleCategoriesReorder"
      />
    </section>
    
    <!-- Best Sellers Section -->
    <section id="bestsellers" class="bestsellers-section">
      <DragDropWidget
        title="Best Sellers"
        subtitle="Our top-selling products loved by customers worldwide"
        :items="bestSellers"
        layout="list"
        :show-controls="false"
        :show-add-button="false"
        @item-action="handleBestSellerAction"
        @items-reordered="handleBestSellersReorder"
      />
    </section>
    
    <Footer 
      brand-name="ShopHub"
      description="Your trusted online shopping destination for quality products at great prices."
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
import { ref } from 'vue'; // <- This was missing!

const navItems = [
  { label: 'Home', href: '#home' },
  { label: 'Products', href: '#products' },
  { label: 'Categories', href: '#categories' },
  { label: 'Best Sellers', href: '#bestsellers' },
  { label: 'About', href: '#about' },
  { label: 'Contact', href: '#contact' }
]

const heroButtons = [
  { text: 'Shop Now', variant: 'primary', action: 'scroll', target: '#products' },
  { text: 'View Categories', variant: 'secondary', action: 'scroll', target: '#categories' }
]

// Featured products with ecommerce styling
const featuredProducts = ref([
  {
    id: 1,
    title: 'Wireless Bluetooth Headphones',
    image: 'https://images.unsplash.com/photo-1505740420928-5e560c06d30e?w=400&h=300&fit=crop',
    description: 'Premium noise-canceling wireless headphones with 30-hour battery life and crystal-clear sound quality.',
    tags: ['Electronics', 'Audio', 'Wireless'],
    price: '$199.99',
    originalPrice: '$299.99',
    discount: '33% OFF',
    button: {
      text: 'Add to Cart',
      variant: 'primary',
      action: 'add-to-cart'
    }
  },
  {
    id: 2,
    title: 'Smart Fitness Watch',
    image: 'https://images.unsplash.com/photo-1523275335684-37898b6baf30?w=400&h=300&fit=crop',
    description: 'Advanced fitness tracking with heart rate monitoring, GPS, and smartphone connectivity.',
    tags: ['Wearables', 'Fitness', 'Smart Tech'],
    price: '$249.99',
    originalPrice: '$349.99',
    discount: '29% OFF',
    button: {
      text: 'Buy Now',
      variant: 'primary',
      action: 'buy-now'
    }
  },
  {
    id: 3,
    title: 'Eco-Friendly Yoga Mat',
    image: 'https://images.unsplash.com/photo-1544367567-0f2fcb009e0b?w=400&h=300&fit=crop',
    description: 'Non-slip, biodegradable yoga mat made from natural rubber with excellent grip and cushioning.',
    tags: ['Fitness', 'Yoga', 'Eco-Friendly'],
    price: '$49.99',
    originalPrice: '$69.99',
    discount: '29% OFF',
    button: {
      text: 'Add to Cart',
      variant: 'primary',
      action: 'add-to-cart'
    }
  },
  {
    id: 4,
    title: 'Organic Skincare Set',
    image: 'https://images.unsplash.com/photo-1596462502278-27bfdc403348?w=400&h=300&fit=crop',
    description: 'Complete organic skincare routine with cleanser, toner, serum, and moisturizer for all skin types.',
    tags: ['Beauty', 'Skincare', 'Organic'],
    price: '$89.99',
    originalPrice: '$129.99',
    discount: '31% OFF',
    button: {
      text: 'Shop Set',
      variant: 'primary',
      action: 'add-to-cart'
    }
  },
  {
    id: 5,
    title: 'Minimalist Desk Lamp',
    image: 'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=400&h=300&fit=crop',
    description: 'LED desk lamp with adjustable brightness, USB charging port, and modern minimalist design.',
    tags: ['Home Office', 'Lighting', 'Modern'],
    price: '$79.99',
    originalPrice: '$99.99',
    discount: '20% OFF',
    button: {
      text: 'Add to Cart',
      variant: 'primary',
      action: 'add-to-cart'
    }
  },
  {
    id: 6,
    title: 'Premium Coffee Beans',
    image: 'https://images.unsplash.com/photo-1559056199-641a0ac8b55e?w=400&h=300&fit=crop',
    description: 'Single-origin, fair-trade coffee beans roasted to perfection for the ultimate coffee experience.',
    tags: ['Coffee', 'Gourmet', 'Fair Trade'],
    price: '$24.99',
    originalPrice: '$34.99',
    discount: '29% OFF',
    button: {
      text: 'Order Now',
      variant: 'primary',
      action: 'add-to-cart'
    }
  }
])

// Product categories
const productCategories = ref([
  {
    id: 1,
    title: 'Electronics & Tech',
    image: 'https://images.unsplash.com/photo-1498049794561-7780e7231661?w=400&h=300&fit=crop',
    description: 'Latest gadgets, smartphones, laptops, and electronic accessories.',
    tags: ['Electronics', 'Gadgets', 'Technology'],
    button: {
      text: 'Browse Electronics',
      variant: 'primary',
      action: 'browse-category',
      category: 'electronics'
    }
  },
  {
    id: 2,
    title: 'Fashion & Clothing',
    image: 'https://images.unsplash.com/photo-1441986300917-64674bd600d8?w=400&h=300&fit=crop',
    description: 'Trendy fashion for men, women, and kids. From casual wear to formal attire.',
    tags: ['Fashion', 'Clothing', 'Style'],
    button: {
      text: 'Shop Fashion',
      variant: 'primary',
      action: 'browse-category',
      category: 'fashion'
    }
  },
  {
    id: 3,
    title: 'Home & Garden',
    image: 'https://images.unsplash.com/photo-1586023492125-27b2c045efd7?w=400&h=300&fit=crop',
    description: 'Everything for your home and garden. Furniture, decor, tools, and more.',
    tags: ['Home', 'Garden', 'Decor'],
    button: {
      text: 'Explore Home',
      variant: 'primary',
      action: 'browse-category',
      category: 'home'
    }
  },
  {
    id: 4,
    title: 'Health & Beauty',
    image: 'https://images.unsplash.com/photo-1556228578-8c89e6adf883?w=400&h=300&fit=crop',
    description: 'Skincare, makeup, wellness products, and health supplements.',
    tags: ['Beauty', 'Health', 'Wellness'],
    button: {
      text: 'Shop Beauty',
      variant: 'primary',
      action: 'browse-category',
      category: 'beauty'
    }
  }
])

// Best sellers
const bestSellers = ref([
  {
    id: 1,
    title: 'Ultra-Soft Bamboo Bed Sheets',
    image: 'https://images.unsplash.com/photo-1631049307264-da0ec9d70304?w=400&h=300&fit=crop',
    description: 'Luxury bamboo bed sheets that are naturally hypoallergenic, breathable, and incredibly soft.',
    tags: ['Bedding', 'Bamboo', 'Luxury'],
    price: '$129.99',
    rating: '4.9/5',
    reviews: '2,847 reviews',
    button: {
      text: 'Best Seller - Order Now',
      variant: 'primary',
      action: 'add-to-cart'
    }
  },
  {
    id: 2,
    title: 'Instant Pot Multi-Cooker',
    image: 'https://images.unsplash.com/photo-1574781330855-d0db8cc6a79c?w=400&h=300&fit=crop',
    description: '7-in-1 electric pressure cooker that replaces multiple kitchen appliances.',
    tags: ['Kitchen', 'Appliances', 'Cooking'],
    price: '$99.99',
    rating: '4.8/5',
    reviews: '15,203 reviews',
    button: {
      text: 'Top Rated - Buy Now',
      variant: 'primary',
      action: 'add-to-cart'
    }
  },
  {
    id: 3,
    title: 'Ergonomic Office Chair',
    image: 'https://images.unsplash.com/photo-1586201375761-83865001e31c?w=400&h=300&fit=crop',
    description: 'Professional office chair with lumbar support and adjustable features for all-day comfort.',
    tags: ['Office', 'Ergonomic', 'Furniture'],
    price: '$299.99',
    rating: '4.7/5',
    reviews: '5,421 reviews',
    button: {
      text: 'Customer Favorite',
      variant: 'primary',
      action: 'add-to-cart'
    }
  }
])

const socialLinks = [
  { platform: 'Facebook', url: 'https://facebook.com/shophub' },
  { platform: 'Instagram', url: 'https://instagram.com/shophub' },
  { platform: 'Twitter', url: 'https://twitter.com/shophub' },
  { platform: 'Pinterest', url: 'https://pinterest.com/shophub' }
]

const footerSections = [
  {
    title: 'Shop',
    links: [
      { text: 'Electronics', href: '#electronics' },
      { text: 'Fashion', href: '#fashion' },
      { text: 'Home & Garden', href: '#home' },
      { text: 'Health & Beauty', href: '#beauty' }
    ]
  },
  {
    title: 'Customer Service',
    links: [
      { text: 'Contact Us', href: '#contact' },
      { text: 'Shipping Info', href: '#shipping' },
      { text: 'Returns', href: '#returns' },
      { text: 'Size Guide', href: '#sizing' }
    ]
  },
  {
    title: 'Company',
    links: [
      { text: 'About Us', href: '#about' },
      { text: 'Careers', href: '#careers' },
      { text: 'Press', href: '#press' },
      { text: 'Sustainability', href: '#sustainability' }
    ]
  }
]

// Event handlers
const handleProductAction = (product) => {
  console.log('Product action:', product.title, product.button?.action)
  
  if (product.button?.action === 'add-to-cart') {
    // Add to cart logic
    alert(`Added "${product.title}" to cart!`)
  } else if (product.button?.action === 'buy-now') {
    // Direct purchase logic
    alert(`Proceeding to checkout for "${product.title}"`)
  }
}

const handleProductsReorder = (reorderedProducts) => {
  console.log('Products reordered:', reorderedProducts.map(p => p.title))
  localStorage.setItem('featuredProductsOrder', JSON.stringify(reorderedProducts))
}

const handleCategoryAction = (category) => {
  console.log('Category action:', category.title, category.button?.category)
  
  if (category.button?.action === 'browse-category') {
    // Navigate to category page
    console.log(`Browsing category: ${category.button.category}`)
  }
}

const handleCategoriesReorder = (reorderedCategories) => {
  console.log('Categories reordered:', reorderedCategories.map(c => c.title))
  localStorage.setItem('productCategoriesOrder', JSON.stringify(reorderedCategories))
}

const handleBestSellerAction = (product) => {
  console.log('Best seller action:', product.title)
  alert(`Added best seller "${product.title}" to cart!`)
}

const handleBestSellersReorder = (reorderedBestSellers) => {
  console.log('Best sellers reordered:', reorderedBestSellers.map(p => p.title))
  localStorage.setItem('bestSellersOrder', JSON.stringify(reorderedBestSellers))
}
</script>

<style scoped>
.products-section {
  padding: 4rem 0;
  background: #f8f9fa;
}

.categories-section {
  padding: 4rem 0;
  background: #ffffff;
}

.bestsellers-section {
  padding: 4rem 0;
  background: #f8f9fa;
}

/* Ecommerce-specific styling */
:deep(.drag-drop-widget .widget-title) {
  color: #2c3e50;
  font-weight: 700;
}

:deep(.drag-drop-widget .tag) {
  background: #28a745;
  color: white;
}

:deep(.drag-drop-widget .item-button.primary) {
  background: #28a745;
  border: none;
  font-weight: 600;
  transition: all 0.3s ease;
}

:deep(.drag-drop-widget .item-button.primary:hover) {
  background: #218838;
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(40, 167, 69, 0.4);
}

:deep(.drag-drop-widget .drag-item) {
  border: 1px solid #e9ecef;
  transition: all 0.3s ease;
}

:deep(.drag-drop-widget .drag-item:hover) {
  border-color: #28a745;
  box-shadow: 0 8px 25px rgba(40, 167, 69, 0.15);
}

/* Add price styling */
:deep(.item-content) {
  position: relative;
}

:deep(.item-content::after) {
  content: attr(data-price);
  position: absolute;
  top: 10px;
  right: 10px;
  background: #dc3545;
  color: white;
  padding: 4px 8px;
  border-radius: 4px;
  font-size: 0.9rem;
  font-weight: bold;
}

@media (max-width: 768px) {
  .products-section,
  .categories-section,
  .bestsellers-section {
    padding: 2rem 0;
  }
}
</style>

