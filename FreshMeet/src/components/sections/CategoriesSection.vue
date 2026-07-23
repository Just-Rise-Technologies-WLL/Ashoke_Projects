<script setup>
import { RouterLink } from 'vue-router'
import { ArrowRight } from 'lucide-vue-next'

const categories = [
  {
    title: 'Fresh Seafood',
    desc: 'Wide range of fresh fish, prawns, and premium seafood caught and delivered daily.',
    svg: `<svg viewBox="0 0 100 100" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="cat-svg">
            <path d="M10,50 Q45,20 85,50 Q45,80 10,50 Z" />
            <path d="M85,50 L95,40 L90,50 L95,60 Z" fill="currentColor" />
            <circle cx="25" cy="46" r="2" fill="currentColor" />
            <path d="M40,32 Q45,40 40,48 M52,32 Q57,40 52,48" stroke-dasharray="1 1" />
          </svg>`
  },
  {
    title: 'Fresh Chicken',
    desc: 'Tender, farm-fresh, and strictly hygienic whole chicken or select cuts for your daily meals.',
    svg: `<svg viewBox="0 0 100 100" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="cat-svg">
            <circle cx="50" cy="50" r="25" />
            <path d="M68,36 Q80,25 76,42 L68,42 Z" fill="currentColor" />
            <path d="M30,55 L20,62 L28,64" />
            <circle cx="58" cy="44" r="2" fill="currentColor" />
            <path d="M50,25 Q53,15 57,25" stroke="#cc2900" stroke-width="3" />
          </svg>`
  },
  {
    title: 'Premium Beef',
    desc: 'High-quality grass-fed beef steaks, ribs, and minced cuts sourced from trusted local farms.',
    svg: `<svg viewBox="0 0 100 100" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="cat-svg">
            <rect x="25" y="35" width="50" height="35" rx="4" />
            <path d="M75,45 Q90,45 85,30 M15,35 L25,42" />
            <!-- Horns -->
            <path d="M28,35 Q20,25 25,18 M38,35 Q38,20 45,22" stroke="currentColor" stroke-width="3" />
            <circle cx="65" cy="45" r="2" fill="currentColor" />
          </svg>`
  },
  {
    title: 'Lamb & Mutton',
    desc: 'Juicy, tender, and flavor-rich mutton ribs, chops, and shoulder cuts prepared under Halal guidelines.',
    svg: `<svg viewBox="0 0 100 100" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="cat-svg">
            <circle cx="50" cy="50" r="28" stroke-dasharray="4 2" />
            <path d="M38,45 C34,45 32,48 32,52 C32,58 38,62 44,62 M62,45 C66,45 68,48 68,52 C68,58 62,62 56,62" />
            <!-- Horns curled -->
            <path d="M42,32 Q35,22 45,15 Q50,22 46,30" stroke="currentColor" stroke-width="2" />
            <circle cx="48" cy="42" r="2" fill="currentColor" />
          </svg>`
  }
]
</script>

<template>
  <section class="categories-section">
    <div class="container">
      
      <div class="section-header">
        <span class="section-subtitle">Our Selections</span>
        <h2 class="section-title">Fresh Meat <span>Categories</span></h2>
      </div>

      <div class="categories-grid">
        <div v-for="(cat, idx) in categories" :key="idx" class="category-card">
          <div class="badge-icon-wrapper" v-html="cat.svg"></div>
          
          <h3 class="category-title">{{ cat.title }}</h3>
          <p class="category-desc">{{ cat.desc }}</p>
          
          <RouterLink to="/products" class="explore-btn">
            View Products <ArrowRight size="16" />
          </RouterLink>
        </div>
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
}

.category-card {
  background-color: white;
  border: 1px solid var(--color-border);
  border-radius: var(--border-radius-md);
  padding: 40px 24px;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  transition: var(--transition-smooth);
}

.category-card:hover {
  transform: translateY(-5px);
  border-color: var(--color-primary);
  box-shadow: 0 12px 30px rgba(0, 71, 27, 0.05);
}

.badge-icon-wrapper {
  background-color: rgba(0, 71, 27, 0.05);
  color: var(--color-primary);
  width: 70px;
  height: 70px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 24px;
  padding: 12px;
  transition: var(--transition-smooth);
}

.category-card:hover .badge-icon-wrapper {
  background-color: var(--color-primary);
  color: white;
  transform: scale(1.08);
}

:deep(.cat-svg) {
  width: 100%;
  height: 100%;
}

.category-title {
  font-size: 18px;
  font-weight: 800;
  color: var(--color-text-dark);
  margin-bottom: 12px;
}

.category-desc {
  font-size: 13px;
  color: var(--color-text-muted);
  line-height: 1.6;
  margin-bottom: 24px;
  flex-grow: 1;
}

.explore-btn {
  font-size: 13px;
  font-weight: 800;
  text-transform: uppercase;
  color: var(--color-accent);
  display: inline-flex;
  align-items: center;
  gap: 6px;
  transition: var(--transition-smooth);
}

.category-card:hover .explore-btn {
  color: var(--color-primary);
}

@media (max-width: 1200px) {
  .categories-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 576px) {
  .categories-grid {
    grid-template-columns: 1fr;
  }
  .categories-section {
    padding: 60px 0;
  }
}
</style>
