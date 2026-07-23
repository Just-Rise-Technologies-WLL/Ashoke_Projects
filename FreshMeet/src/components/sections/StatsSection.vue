<script setup>
import { Users, Truck, Smile, ShieldCheck } from 'lucide-vue-next'

const stats = [
  {
    icon: Smile,
    num: '500+',
    label: 'Happy Clients'
  },
  {
    icon: Users,
    num: '1500+',
    label: 'Deliveries Daily (KG)'
  },
  {
    icon: Truck,
    num: '25+',
    label: 'Delivery Vehicles'
  },
  {
    icon: ShieldCheck,
    num: '100%',
    label: 'Quality Guaranteed'
  }
]
</script>

<template>
  <section class="stats-section">
    <div class="container stats-container">
      <div v-for="(stat, idx) in stats" :key="idx" class="stat-item">
        <component :is="stat.icon" size="40" class="stat-icon" />
        <div class="stat-content">
          <div class="stat-num">{{ stat.num }}</div>
          <div class="stat-label">{{ stat.label }}</div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.stats-section {
  background-color: var(--color-dark);
  color: white;
  padding: 40px 0;
  border-top: 1px solid rgba(255, 255, 255, 0.05);
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
}

.stats-container {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 30px;
}

.stat-item {
  display: flex;
  align-items: center;
  gap: 16px;
  flex: 1;
  min-width: 200px;
}

.stat-icon {
  color: var(--color-accent);
}

.stat-num {
  font-size: 32px;
  font-weight: 900;
  line-height: 1.2;
}

.stat-label {
  font-size: 13px;
  color: var(--color-text-light);
  font-weight: 500;
}

@media (max-width: 768px) {
  .stats-container {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 24px 16px;
  }
}

@media (max-width: 480px) {
  .stats-container {
    grid-template-columns: 1fr;
  }
}
</style>
