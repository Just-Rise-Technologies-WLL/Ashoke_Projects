<script setup>
import { ShieldCheck, Layers, Truck, Headset } from 'lucide-vue-next'

const features = [
  {
    icon: ShieldCheck,
    title: 'High Quality Parts',
    desc: '100% Genuine & Reliable'
  },
  {
    icon: Layers,
    title: 'Wide Range',
    desc: 'Thousands of Parts'
  },
  {
    icon: Truck,
    title: 'Fast Delivery',
    desc: 'On Time, Every Time'
  },
  {
    icon: Headset,
    title: 'Expert Support',
    desc: "We're Here to Help"
  }
]
</script>

<template>
  <section class="features-section">
    <div class="container features-container">
      <div v-for="(feat, idx) in features" :key="idx" class="feature-item">
        <div class="icon-wrapper">
          <component :is="feat.icon" size="28" class="feat-icon" />
        </div>
        <div class="feat-content">
          <h3 class="feat-title">{{ feat.title }}</h3>
          <p class="feat-desc">{{ feat.desc }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.features-section {
  background-color: var(--color-light);
  margin-top: -40px; /* Overlap hero slightly */
  position: relative;
  z-index: 15;
  max-width: var(--max-width);
  margin-left: auto;
  margin-right: auto;
  padding: 30px;
  border-radius: var(--border-radius-md);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
  border: 1px solid var(--color-border);
}

.features-container {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 20px;
}

.feature-item {
  display: flex;
  align-items: center;
  gap: 16px;
  flex: 1;
  min-width: 230px;
  padding: 10px;
  transition: var(--transition-smooth);
}

.feature-item:hover {
  transform: translateY(-2px);
}

.icon-wrapper {
  background-color: rgba(220, 38, 38, 0.08);
  width: 54px;
  height: 54px;
  border-radius: var(--border-radius-sm);
  display: flex;
  justify-content: center;
  align-items: center;
  transition: var(--transition-smooth);
}

.feature-item:hover .icon-wrapper {
  background-color: var(--color-primary);
}

.feat-icon {
  color: var(--color-primary);
  stroke-width: 1.8;
  transition: var(--transition-smooth);
}

.feature-item:hover .feat-icon {
  color: white;
}

.feat-title {
  font-size: 15px;
  font-weight: 800;
  text-transform: uppercase;
  color: var(--color-text-dark);
  margin-bottom: 2px;
  letter-spacing: 0.5px;
}

.feat-desc {
  font-size: 13px;
  color: var(--color-text-muted);
  font-weight: 500;
}

@media (max-width: 1200px) {
  .features-section {
    margin-left: 20px;
    margin-right: 20px;
  }
}

@media (max-width: 768px) {
  .features-section {
    margin-top: 0;
    border-radius: 0;
    border-left: none;
    border-right: none;
  }
}

@media (max-width: 576px) {
  .features-container {
    display: grid;
    grid-template-columns: 1fr;
    gap: 16px;
  }
}
</style>
