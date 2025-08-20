# Landing Page Templates

A collection of modern, responsive landing page templates built with Vue.js and Vite. This project includes three different landing page themes: Coach, Agency, and E-commerce, all sharing a common set of reusable components.

## 🚀 Features

- **Three Landing Page Themes:**
  - **Coach Landing**: Professional coaching services
  - **Agency Landing**: Creative agency portfolio
  - **E-commerce Landing**: Online store storefront

- **Shared Component Architecture:**
  - Reusable Header, Hero, and Footer components
  - Customizable props for different themes
  - Responsive design for all screen sizes

- **Modern Tech Stack:**
  - Vue.js 3 with Composition API
  - Vite for fast development and building
  - CSS Grid and Flexbox for layouts
  - Mobile-first responsive design

## 📁 Project Structure

```
landing-templates/
├── shared/
│   └── components/
│       ├── Header.vue
│       ├── Hero.vue
│       └── Footer.vue
├── coach-landing/
│   ├── App.vue
│   ├── main.js
│   ├── index.html
│   └── vite.config.mjs
├── agency-landing/
│   ├── App.vue
│   ├── main.js
│   ├── index.html
│   └── vite.config.mjs
├── ecommerce-landing/
│   ├── App.vue
│   ├── main.js
│   ├── index.html
│   └── vite.config.mjs
├── package.json
├── README.md
└── .gitignore
```

## 🛠️ Installation

1. **Clone the repository:**
   ```bash
   git clone <your-repo-url>
   cd landing-templates
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

## 🚀 Development

Run any of the three landing pages in development mode:

```bash
# Coach landing page
npm run dev:coach

# Agency landing page
npm run dev:agency

# E-commerce landing page
npm run dev:ecommerce
```

Each command will start a development server (usually at `http://localhost:5173`) with hot module replacement.

## 🎨 Customization

### Shared Components

All three landing pages use shared components located in the `shared/components/` directory:

#### Header Component
- Customizable logo and navigation items
- Responsive mobile menu
- Call-to-action button

#### Hero Component
- Flexible title and subtitle
- Multiple button configurations
- Background color/gradient customization
- Optional hero image
- Theme variants (coach, agency, ecommerce)

#### Footer Component
- Dynamic sections and links
- Social media links
- Brand information
- Responsive layout

### Theme Customization

Each landing page can be customized by modifying the props passed to the shared components:

```vue
<Hero 
  title="Your Custom Title"
  subtitle="Your custom subtitle"
  :buttons="customButtons"
  background-color="linear-gradient(135deg, #your-colors)"
  theme="coach|agency|ecommerce"
/>
```

## 📱 Responsive Design

All templates are built with mobile-first responsive design:

- **Mobile**: < 768px
- **Tablet**: 768px - 1024px
- **Desktop**: > 1024px

## 🎯 Landing Page Themes

### Coach Landing (CoachPro)
Perfect for life coaches, business coaches, and consultants:
- Professional gradient background
- Service-focused navigation
- Call-to-action for booking sessions

### Agency Landing (CreativeHub)
Ideal for creative agencies and design studios:
- Modern typography
- Portfolio-focused navigation
- Project inquiry call-to-action

### E-commerce Landing (ShopVibe)
Great for online stores and product showcases:
- Product-focused design
- Shopping-oriented navigation
- Purchase-driven call-to-action

## 🔧 Configuration

### Vite Configuration

Each landing page has its own `vite.config.mjs` with alias configuration for shared components:

```javascript
import { defineConfig } from "vite";
import vue from "@vitejs/plugin-vue";
import { fileURLToPath, URL } from 'node:url';

export default defineConfig({
  plugins: [vue()],
  resolve: {
    alias: {
      "@shared": fileURLToPath(new URL("../shared", import.meta.url)),
    },
  },
});
```

## 📦 Building for Production

To build any landing page for production:

```bash
# Navigate to the specific landing page directory
cd coach-landing
# or
cd agency-landing
# or
cd ecommerce-landing

# Build for production
npx vite build
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/new-feature`
3. Commit your changes: `git commit -am 'Add new feature'`
4. Push to the branch: `git push origin feature/new-feature`
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

If you encounter any issues or have questions:

1. Check the [Issues](../../issues) page
2. Create a new issue if your problem isn't already reported
3. Provide detailed information about your setup and the issue

## 🚀 Future Enhancements

- [ ] Add more theme variations
- [ ] Include additional shared components (testimonials, pricing, etc.)
- [ ] Add animation libraries integration
- [ ] Include SEO optimization features
- [ ] Add TypeScript support
- [ ] Include unit tests

---

Built with ❤️ using Vue.js and Vite