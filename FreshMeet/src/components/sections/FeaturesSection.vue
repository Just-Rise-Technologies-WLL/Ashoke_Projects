<script setup>
import { ShieldCheck, Snowflake, Utensils, Award } from 'lucide-vue-next'

const features = [
  {
    icon: Snowflake,
    title: '100% Fresh',
    desc: 'Always Fresh, Never Frozen'
  },
  {
    icon: Utensils,
    title: 'Halal Certified',
    desc: 'Halal & Hygienic Process'
  },
  {
    icon: ShieldCheck,
    title: 'Cold Chain Delivery',
    desc: 'Maintained Freshness'
  },
  {
    icon: Award,
    title: 'Best Quality',
    desc: 'Premium & Trusted'
  }
]
</script>

<template>
  <section class="features-section">
    <div class="container features-container">
      <div v-for="(feat, idx) in features" :key="idx" class="feature-item">
        <div class="icon-wrapper">
          <component :is="feat.icon" size="24" class="feat-icon" />
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
  background-color: var(--color-dark-surface);
  border-top: 1px solid rgba(255, 255, 255, 0.05);
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
  padding: 30px 0;
  position: relative;
  z-index: 10;
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
  color: white;
  padding: 10px;
  transition: var(--transition-smooth);
}

.feature-item:hover {
  transform: translateY(-2px);
}

.icon-wrapper {
  background-color: rgba(204, 41, 0, 0.1);
  width: 50px;
  height: 50px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  border: 1px solid rgba(204, 41, 0, 0.2);
  transition: var(--transition-smooth);
}

.feature-item:hover .icon-wrapper {
  background-color: var(--color-accent);
  border-color: var(--color-accent);
}

.feat-icon {
  color: var(--color-accent);
  transition: var(--transition-smooth);
}

.feature-item:hover .feat-icon {
  color: white;
}

.feat-title {
  font-size: 15px;
  font-weight: 800;
  text-transform: uppercase;
  margin-bottom: 2px;
  letter-spacing: 0.5px;
}

.feat-desc {
  font-size: 13px;
  color: var(--color-text-light);
}

@media (max-width: 576px) {
  .features-container {
    display: grid;
    grid-template-columns: 1fr;
    gap: 16px;
  }
}
</style>
