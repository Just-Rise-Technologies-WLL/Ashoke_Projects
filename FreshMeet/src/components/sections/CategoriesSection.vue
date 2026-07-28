<script setup>
import { RouterLink } from 'vue-router'
import { ArrowRight, Fish, Bird, Beef, Drumstick } from 'lucide-vue-next'

const categories = [
  {
    title: 'FRESH SEAFOOD',
    desc: 'Wide range of fresh fish, prawns, and seafood delivered daily.',
    image: '/images/raw_fresh_seafood.png',
    icon: Fish
  },
  {
    title: 'FRESH CHICKEN',
    desc: 'Tender and hygienic chicken, perfect for your daily needs.',
    image: '/images/raw_farm_chicken.png',
    icon: Bird
  },
  {
    title: 'PREMIUM BEEF',
    desc: 'High quality beef cuts sourced from trusted suppliers.',
    image: '/images/raw_beef_steak.png',
    icon: Beef
  },
  {
    title: 'LAMB & MUTTON',
    desc: 'Juicy and tender mutton cuts for a rich and delicious taste.',
    image: '/images/raw_lamb_chops.png',
    icon: Drumstick
  }
]
</script>

<template>
  <section class="categories-section">
    <div class="container">
      
      <div class="categories-grid">
        <div v-for="(cat, idx) in categories" :key="idx" class="category-card">
          <!-- Card Top Image with Overlapping Icon Badge -->
          <div class="card-image-wrap">
            <img :src="cat.image" :alt="cat.title" class="card-img" />
            <div class="badge-icon-overlay">
              <component :is="cat.icon" size="20" />
            </div>
          </div>
          
          <div class="card-body">
            <h3 class="category-title">{{ cat.title }}</h3>
            <p class="category-desc">{{ cat.desc }}</p>
            
            <RouterLink to="/products" class="explore-btn">
              VIEW PRODUCTS <ArrowRight size="14" />
            </RouterLink>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>

<style scoped>
.categories-section {
  background-color: #f8fafc;
  padding: 70px 0;
}

.categories-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 24px;
}

.category-card {
  background-color: white;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
  display: flex;
  flex-direction: column;
  transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
  border: 1px solid #e2e8f0;
}

.category-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 20px 35px rgba(204, 41, 0, 0.12);
  border-color: rgba(204, 41, 0, 0.3);
}

.card-image-wrap {
  position: relative;
  height: 200px;
  overflow: hidden;
}

.card-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.6s ease;
}

.category-card:hover .card-img {
  transform: scale(1.08);
}

.badge-icon-overlay {
  position: absolute;
  bottom: 12px;
  left: 20px;
  width: 44px;
  height: 44px;
  border-radius: 50%;
  background-color: #cc2900;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 12px rgba(204, 41, 0, 0.4);
  border: 2px solid white;
  transition: transform 0.3s ease;
}

.category-card:hover .badge-icon-overlay {
  transform: scale(1.1) rotate(5deg);
}

.card-body {
  padding: 24px;
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

.category-title {
  font-size: 17px;
  font-weight: 900;
  color: #0f172a;
  margin-bottom: 10px;
  letter-spacing: -0.3px;
  text-transform: uppercase;
}

.category-desc {
  font-size: 13px;
  color: #64748b;
  line-height: 1.6;
  margin-bottom: 20px;
  flex-grow: 1;
}

.explore-btn {
  font-size: 12px;
  font-weight: 800;
  text-transform: uppercase;
  color: #cc2900;
  display: inline-flex;
  align-items: center;
  gap: 6px;
  letter-spacing: 0.5px;
  transition: gap 0.3s ease;
}

.category-card:hover .explore-btn {
  gap: 10px;
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
    padding: 50px 0;
  }
}
</style>

