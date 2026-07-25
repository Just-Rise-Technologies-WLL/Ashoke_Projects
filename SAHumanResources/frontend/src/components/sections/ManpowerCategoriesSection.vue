<script setup>
import SectionHeader from '../ui/SectionHeader.vue'
import Button from '../ui/Button.vue'
import { ArrowRight } from 'lucide-vue-next'

const categories = [
  { title: 'Aluminium Fitter', img: '/images/categories/aluminium_fitter.jpg' },
  { title: 'Setting Carpenter', img: '/images/categories/setting_carpenter.jpg' },
  { title: 'Mason', img: '/images/categories/mason.jpg' },
  { title: 'Welder', img: '/images/categories/welder.jpg' },
  { title: 'Electrician', img: '/images/categories/electrician.jpg' },
  { title: 'Plumber', img: '/images/categories/plumber.jpg' }
]
</script>

<template>
  <section class="categories-section">
    <div class="container">
      <SectionHeader subtitle="MANPOWER CATEGORIES" title="" :centered="true" />
      <p class="section-subtitle">Skilled and semi-skilled professionals for every construction need</p>
      
      <div class="categories-grid">
        <div 
          v-for="(cat, index) in categories" 
          :key="index" 
          class="category-card"
        >
          <div class="card-image" :style="{ backgroundImage: 'url(' + cat.img + ')' }"></div>
          <div class="card-content">
            <h3 class="cat-title">{{ cat.title }}</h3>
          </div>
        </div>
      </div>

      <div class="action-footer">
        <Button to="/industries" variant="primary" class="view-all-btn">
          VIEW ALL CATEGORIES <ArrowRight size="18" />
        </Button>
      </div>
    </div>
  </section>
</template>

<style scoped>
.categories-section {
  padding: 80px 0;
  background-color: white;
}

.section-subtitle {
  text-align: center;
  color: var(--color-text-muted);
  margin-top: -30px;
  margin-bottom: 50px;
  font-size: 16px;
}

.categories-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
  margin-bottom: 48px;
}

.category-card {
  height: 220px;
  border-radius: var(--border-radius);
  position: relative;
  overflow: hidden;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.card-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  transition: transform 0.6s cubic-bezier(0.4, 0, 0.2, 1);
  z-index: 1;
}

.category-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 25px rgba(0, 71, 27, 0.12);
}

.category-card:hover .card-image {
  transform: scale(1.08);
}

.card-content {
  position: absolute;
  top: 16px;
  right: 16px;
  z-index: 2;
}

.cat-title {
  background-color: var(--color-primary);
  color: white;
  font-size: 13px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  margin: 0;
  padding: 8px 18px;
  border-radius: 100px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.15);
  display: inline-block;
  transition: all 0.3s ease;
}

.category-card:hover .cat-title {
  background-color: var(--color-accent);
  transform: translateY(-2px);
  box-shadow: 0 6px 15px rgba(109, 181, 53, 0.3);
}

.action-footer {
  text-align: center;
}

.view-all-btn {
  padding: 14px 36px;
}

@media (max-width: 992px) {
  .categories-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
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
