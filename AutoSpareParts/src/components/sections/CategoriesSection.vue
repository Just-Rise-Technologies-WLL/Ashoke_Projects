<script setup>
import { RouterLink } from 'vue-router'
import { ArrowRight } from 'lucide-vue-next'

const categories = [
  {
    title: 'Engine Parts',
    svg: `<svg viewBox="0 0 100 100" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="category-icon-svg">
            <rect x="25" y="30" width="50" height="40" rx="4" />
            <circle cx="37" cy="50" r="6" />
            <circle cx="63" cy="50" r="6" />
            <path d="M50,20 L50,30 M30,20 L35,30 M70,20 L65,30 M15,50 L25,50 M75,50 L85,50" />
          </svg>`
  },
  {
    title: 'Brake System',
    svg: `<svg viewBox="0 0 100 100" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="category-icon-svg">
            <circle cx="50" cy="50" r="32" />
            <circle cx="50" cy="50" r="20" stroke-dasharray="3 3" />
            <circle cx="50" cy="50" r="8" fill="currentColor" />
            <path d="M74,26 C82,34 82,48 76,60" stroke="#dc2626" stroke-width="6" />
          </svg>`
  },
  {
    title: 'Suspension Parts',
    svg: `<svg viewBox="0 0 100 100" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="category-icon-svg">
            <line x1="50" y1="15" x2="50" y2="25" />
            <path d="M35,25 C35,25 45,30 50,30 C55,30 65,25 65,25 C65,25 55,35 50,35 C45,35 35,25 35,25 Z M35,40 C35,40 45,45 50,45 C55,45 65,40 65,40 C65,40 55,50 50,50 C45,50 35,40 35,40 Z M35,55 C35,55 45,60 50,60 C55,60 65,55 65,55 C65,55 55,65 50,65 C45,65 35,55 35,55 Z" />
            <line x1="50" y1="65" x2="50" y2="85" />
          </svg>`
  },
  {
    title: 'Filters',
    svg: `<svg viewBox="0 0 100 100" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="category-icon-svg">
            <rect x="30" y="15" width="40" height="70" rx="6" />
            <line x1="30" y1="30" x2="70" y2="30" />
            <line x1="30" y1="45" x2="70" y2="45" stroke-dasharray="2 2" />
            <line x1="30" y1="60" x2="70" y2="60" stroke-dasharray="2 2" />
            <line x1="30" y1="75" x2="70" y2="75" />
          </svg>`
  },
  {
    title: 'Electrical Parts',
    svg: `<svg viewBox="0 0 100 100" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="category-icon-svg">
            <rect x="25" y="25" width="50" height="50" rx="4" />
            <line x1="35" y1="15" x2="35" y2="25" stroke-width="4" />
            <line x1="65" y1="15" x2="65" y2="25" stroke-width="4" />
            <text x="31" y="22" font-size="10" font-weight="900" fill="currentColor">-</text>
            <text x="59" y="23" font-size="10" font-weight="900" fill="currentColor">+</text>
            <path d="M50,38 L43,50 L57,50 L50,62" stroke="#dc2626" stroke-width="3" />
          </svg>`
  },
  {
    title: 'Body Parts',
    svg: `<svg viewBox="0 0 100 100" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="category-icon-svg">
            <path d="M15,50 C25,48 75,48 85,50 L90,62 C90,62 80,68 50,68 C20,68 10,62 10,62 Z" />
            <rect x="30" y="54" width="40" height="8" rx="2" />
            <circle cx="22" cy="56" r="3" fill="currentColor" />
            <circle cx="78" cy="56" r="3" fill="currentColor" />
          </svg>`
  },
  {
    title: 'Oils & Fluids',
    svg: `<svg viewBox="0 0 100 100" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="category-icon-svg">
            <path d="M35,35 L35,80 C35,83 37,85 40,85 L70,85 C73,85 75,83 75,80 L75,35 Z" />
            <path d="M45,35 L48,20 L58,20 L55,35 Z" />
            <circle cx="55" cy="60" r="10" stroke="#dc2626" />
            <path d="M55,54 L55,66 M49,60 L61,60" stroke="#dc2626" />
          </svg>`
  },
  {
    title: 'Accessories',
    svg: `<svg viewBox="0 0 100 100" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="category-icon-svg">
            <circle cx="50" cy="50" r="35" />
            <circle cx="50" cy="50" r="28" stroke-dasharray="2 4" />
            <line x1="50" y1="15" x2="50" y2="85" />
            <line x1="15" y1="50" x2="85" y2="50" />
            <circle cx="50" cy="50" r="8" fill="currentColor" />
          </svg>`
  }
]
</script>

<template>
  <section class="categories-section">
    <div class="container">
      
      <div class="section-header">
        <span class="section-subtitle">Premium Selections</span>
        <h2 class="section-title">Our Product <span>Categories</span></h2>
      </div>

      <div class="categories-grid">
        <RouterLink 
          v-for="(cat, idx) in categories" 
          :key="idx" 
          to="/products"
          class="category-card"
        >
          <div class="svg-container" v-html="cat.svg"></div>
          <h3 class="category-title">{{ cat.title }}</h3>
          <span class="explore-link">Explore Category <ArrowRight size="14" /></span>
        </RouterLink>
      </div>

      <div class="action-footer">
        <RouterLink to="/products" class="btn btn-primary view-all-btn">
          View All Products <ArrowRight size="18" />
        </RouterLink>
      </div>

    </div>
  </section>
</template>

<style scoped>
.categories-section {
  background-color: var(--color-light-surface);
  padding: 80px 0;
}

.categories-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 24px;
  margin-bottom: 48px;
}

.category-card {
  background-color: var(--color-light);
  border: 1px solid var(--color-border);
  border-radius: var(--border-radius-md);
  padding: 30px 20px;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  transition: var(--transition-smooth);
}

.category-card:hover {
  transform: translateY(-5px);
  border-color: var(--color-primary);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.05);
}

.svg-container {
  color: var(--color-text-dark);
  width: 70px;
  height: 70px;
  margin-bottom: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: var(--transition-smooth);
}

.category-card:hover .svg-container {
  color: var(--color-primary);
  transform: scale(1.1);
}

:deep(.category-icon-svg) {
  width: 100%;
  height: 100%;
}

.category-title {
  font-size: 18px;
  font-weight: 800;
  color: var(--color-text-dark);
  margin-bottom: 12px;
}

.explore-link {
  font-size: 13px;
  font-weight: 700;
  color: var(--color-text-muted);
  display: inline-flex;
  align-items: center;
  gap: 4px;
  text-transform: uppercase;
  transition: var(--transition-smooth);
}

.category-card:hover .explore-link {
  color: var(--color-primary);
}

.action-footer {
  text-align: center;
}

.view-all-btn {
  padding: 14px 32px;
}

@media (max-width: 1200px) {
  .categories-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media (max-width: 768px) {
  .categories-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 16px;
  }
  .categories-section {
    padding: 60px 0;
  }
}

@media (max-width: 480px) {
  .categories-grid {
    grid-template-columns: 1fr;
  }
}
</style>
