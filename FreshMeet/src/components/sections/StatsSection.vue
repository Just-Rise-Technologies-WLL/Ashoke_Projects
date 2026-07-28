<script setup>
import { Users, PackageCheck, Truck, ShieldCheck } from 'lucide-vue-next'

const stats = [
  {
    icon: Users,
    num: '500+',
    label: 'Happy Clients'
  },
  {
    icon: PackageCheck,
    num: '1500+',
    label: 'Products Delivered Daily'
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
        <component :is="stat.icon" size="32" class="stat-icon" />
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
  background-color: #0c0d0e;
  color: white;
  padding: 36px 0;
  border-top: 1px solid rgba(255, 255, 255, 0.08);
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
}

.stats-container {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
}

.stat-item {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 16px;
  position: relative;
}

.stat-item:not(:last-child)::after {
  content: '';
  position: absolute;
  right: 0;
  top: 15%;
  height: 70%;
  width: 1px;
  background-color: rgba(255, 255, 255, 0.12);
}

.stat-icon {
  color: #cc2900;
  flex-shrink: 0;
}

.stat-num {
  font-size: 32px;
  font-weight: 900;
  line-height: 1.1;
  color: white;
}

.stat-label {
  font-size: 13px;
  color: #9ca3af;
  font-weight: 500;
  margin-top: 2px;
}

@media (max-width: 992px) {
  .stats-container {
    grid-template-columns: repeat(2, 1fr);
    gap: 30px;
  }
  .stat-item:not(:last-child)::after {
    display: none;
  }
}

@media (max-width: 576px) {
  .stats-container {
    grid-template-columns: 1fr;
    gap: 24px;
  }
}
</style>

