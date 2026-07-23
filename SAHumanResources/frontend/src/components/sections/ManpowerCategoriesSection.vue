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
          :style="{ backgroundImage: 'linear-gradient(to top, rgba(0, 71, 27, 0.85) 0%, rgba(0, 0, 0, 0.3) 70%), url(' + cat.img + ')' }"
        >
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
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  border-radius: var(--border-radius);
  position: relative;
  overflow: hidden;
  display: flex;
  align-items: flex-end;
  padding: 24px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.category-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 71, 27, 0.1);
  transition: all 0.4s ease;
  z-index: 1;
}

.category-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 25px rgba(0, 71, 27, 0.15);
}

.category-card:hover::before {
  background-color: rgba(0, 71, 27, 0);
}

.card-content {
  position: relative;
  z-index: 2;
}

.cat-title {
  color: white;
  font-size: 20px;
  font-weight: 800;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  margin: 0;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
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
