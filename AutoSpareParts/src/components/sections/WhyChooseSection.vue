<script setup>
import { ShieldCheck, Tags, Handshake, Users } from 'lucide-vue-next'

const reasons = [
  {
    icon: ShieldCheck,
    title: 'Genuine Quality',
    desc: 'Only genuine and high-quality OEM or certified aftermarket parts.'
  },
  {
    icon: Tags,
    title: 'Affordable Prices',
    desc: 'Competitive wholesale and retail pricing for maximum value.'
  },
  {
    icon: Handshake,
    title: 'Trusted Partner',
    desc: 'Serving customers across the GCC with honesty, transparency, and integrity.'
  },
  {
    icon: Users,
    title: 'Experienced Team',
    desc: 'Industry parts specialists ready to assist with fitment identification.'
  }
]
</script>

<template>
  <section class="why-choose-section">
    <!-- Grid layout overlay with a dark premium car shape styled in CSS -->
    <div class="vector-backdrop"></div>
    
    <div class="container choose-inner">
      <div class="choose-text animate-fade-in">
        <span class="section-subtitle">Why Choose Us</span>
        <h2 class="section-title dark-title">Why Choose <span>MTN?</span></h2>
        <p class="choose-desc">
          We are committed to supplying the absolute best automotive components in the region. Our robust supply chain makes us the preferred choice for workshops, fleets, and retailers.
        </p>
        
        <!-- Car Front Outline Drawing in SVG (no image url) -->
        <svg viewBox="0 0 200 80" width="100%" class="car-outline-svg">
          <path d="M20,60 L40,60 C42,60 45,55 48,50 L152,50 C155,55 158,60 160,60 L180,60 C190,60 195,55 195,45 L190,30 C188,25 180,18 165,18 L155,18 C145,18 135,10 115,10 L85,10 C65,10 55,18 45,18 L35,18 C20,18 12,25 10,30 L5,45 C5,55 10,60 20,60 Z" fill="none" stroke="rgba(220, 38, 38, 0.15)" stroke-width="2" />
          <!-- Headlights -->
          <path d="M12,42 L25,44 L25,48 L12,48 Z" fill="none" stroke="rgba(220, 38, 38, 0.3)" stroke-width="1.5" />
          <path d="M188,42 L175,44 L175,48 L188,48 Z" fill="none" stroke="rgba(220, 38, 38, 0.3)" stroke-width="1.5" />
          <!-- Wheels -->
          <circle cx="45" cy="62" r="10" fill="none" stroke="rgba(255, 255, 255, 0.2)" stroke-width="2" />
          <circle cx="155" cy="62" r="10" fill="none" stroke="rgba(255, 255, 255, 0.2)" stroke-width="2" />
        </svg>
      </div>

      <div class="reasons-grid">
        <div v-for="(reason, idx) in reasons" :key="idx" class="reason-card">
          <div class="icon-box">
            <component :is="reason.icon" size="24" class="reason-icon" />
          </div>
          <div class="reason-content">
            <h3 class="reason-title">{{ reason.title }}</h3>
            <p class="reason-desc-text">{{ reason.desc }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.why-choose-section {
  background-color: var(--color-dark);
  color: white;
  padding: 100px 0;
  position: relative;
  overflow: hidden;
}

.vector-backdrop {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: radial-gradient(circle at 10% 20%, rgba(220, 38, 38, 0.05) 0%, transparent 60%);
  pointer-events: none;
}

.choose-inner {
  display: grid;
  grid-template-columns: 0.9fr 1.1fr;
  gap: 60px;
  align-items: center;
}

.dark-title {
  color: white;
}

.dark-title::after {
  margin: 12px 0 0;
}

.choose-desc {
  font-size: 16px;
  line-height: 1.6;
  color: var(--color-text-light);
  margin-top: 24px;
  margin-bottom: 30px;
}

.car-outline-svg {
  max-width: 320px;
  margin-top: 10px;
}

.reasons-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 24px;
}

.reason-card {
  background-color: var(--color-dark-surface);
  border: 1px solid rgba(255, 255, 255, 0.05);
  border-radius: var(--border-radius-md);
  padding: 30px 24px;
  display: flex;
  flex-direction: column;
  gap: 16px;
  transition: var(--transition-smooth);
}

.reason-card:hover {
  transform: translateY(-4px);
  border-color: rgba(220, 38, 38, 0.3);
}

.icon-box {
  background-color: rgba(220, 38, 38, 0.1);
  width: 48px;
  height: 48px;
  border-radius: var(--border-radius-sm);
  display: flex;
  justify-content: center;
  align-items: center;
  border: 1px solid rgba(220, 38, 38, 0.2);
}

.reason-icon {
  color: var(--color-primary);
}

.reason-title {
  font-size: 18px;
  font-weight: 700;
  color: white;
  margin-bottom: 6px;
}

.reason-desc-text {
  font-size: 14px;
  color: var(--color-text-light);
  line-height: 1.5;
}

@media (max-width: 992px) {
  .choose-inner {
    grid-template-columns: 1fr;
    gap: 40px;
  }
  .dark-title::after {
    margin: 12px auto 0;
  }
  .choose-text {
    text-align: center;
  }
  .car-outline-svg {
    margin-left: auto;
    margin-right: auto;
  }
}

@media (max-width: 576px) {
  .reasons-grid {
    grid-template-columns: 1fr;
  }
  .why-choose-section {
    padding: 60px 0;
  }
}
</style>
