<script setup>
import SectionHeader from '../ui/SectionHeader.vue'
import Button from '../ui/Button.vue'
import { ArrowRight, Wrench, Hammer, Monitor, Blocks, Zap, Wind, Droplets, PaintRoller, User } from 'lucide-vue-next'

const categories = [
  { icon: Blocks, title: 'Aluminium Fitter' },
  { icon: Hammer, title: 'Setting Carpenter' },
  { icon: Wrench, title: 'Furniture Carpenter' },
  { icon: Wrench, title: 'Mason' },
  { icon: Zap, title: 'Rigger' },
  { icon: Zap, title: 'Steel Fixer' },
  { icon: Droplets, title: 'Pipe Fitter' },
  { icon: Wrench, title: 'Welder' },
  { icon: Zap, title: 'Electrician' },
  { icon: Wind, title: 'Ductman' },
  { icon: Droplets, title: 'Plumber' },
  { icon: PaintRoller, title: 'Painter' },
  { icon: User, title: 'Helper' }
]
</script>

<template>
  <section class="categories-section">
    <div class="container">
      <SectionHeader subtitle="MANPOWER CATEGORIES" title="" :centered="true" />
      <p class="section-subtitle">Skilled and semi-skilled professionals for every construction need</p>
      
      <div class="categories-grid">
        <div v-for="(cat, index) in categories" :key="index" class="category-item">
          <component :is="cat.icon" size="24" class="cat-icon" />
          <span class="cat-title">{{ cat.title }}</span>
        </div>
        
        <div class="category-item more-item">
          <Users size="24" class="cat-icon white" />
          <span class="cat-title white">... And More Skilled Workers</span>
        </div>
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
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 20px;
}

.category-item {
  border: 1px solid var(--color-border);
  border-radius: var(--border-radius);
  padding: 20px;
  display: flex;
  align-items: center;
  gap: 15px;
  transition: all 0.3s ease;
  background-color: white;
}

.category-item:hover:not(.more-item) {
  border-color: var(--color-accent);
  box-shadow: var(--shadow-md);
  transform: translateY(-2px);
}

.cat-icon {
  color: var(--color-accent);
}

.cat-title {
  font-weight: 600;
  color: var(--color-text-main);
  font-size: 15px;
}

.more-item {
  background-color: var(--color-primary-dark);
  border-color: var(--color-primary-dark);
  grid-column: span 2;
  justify-content: center;
}

.white {
  color: white !important;
}

@media (max-width: 576px) {
  .more-item {
    grid-column: span 1;
  }
}
</style>
