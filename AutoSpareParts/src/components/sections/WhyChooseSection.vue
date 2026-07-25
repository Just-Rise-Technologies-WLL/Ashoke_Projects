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
        
        <!-- Animated Car SVG (profile view of a sleek sports car) -->
        <svg viewBox="0 0 200 85" width="100%" class="car-outline-svg">
          <!-- Road line moving to simulate speed -->
          <line x1="0" y1="71" x2="200" y2="71" stroke="rgba(255, 255, 255, 0.2)" stroke-width="2" stroke-dasharray="8 6" class="road-line" />
          
          <!-- Car chassis and lights group (bounces slightly) -->
          <g class="car-chassis">
            <!-- Main sports car body outline with wheel arches -->
            <path d="M 15,60 C 10,60 10,48 15,48 L 25,48 C 30,48 35,45 40,42 C 55,30 65,22 80,22 L 120,22 C 135,22 145,30 155,40 L 175,43 C 185,43 190,46 190,52 L 185,60 L 162,60 C 162,47 138,47 138,60 L 62,60 C 62,47 38,47 38,60 L 15,60 Z" fill="none" class="car-body" />
                  
            <!-- Side window outline -->
            <path d="M 75,26 L 118,26 C 128,26 135,31 141,37 L 143,39 L 75,39 Z" fill="none" class="car-window" />
            <!-- Door pillar/divider -->
            <line x1="110" y1="26" x2="110" y2="39" class="car-window-divider" />
            
            <!-- Sleek Headlight (Front, right) -->
            <path d="M 178,44 L 187,46 C 187,48 185,50 183,50 L 176,48 Z" fill="none" class="car-headlight" />
            <!-- Tail light (Rear, left) -->
            <path d="M 14,48 L 22,48 L 20,52 L 13,52 Z" fill="none" class="car-taillight" />
          </g>
          
          <!-- Rotating Wheels (spokes detail for rotation visibility) -->
          <g class="car-wheel wheel-front">
            <circle cx="150" cy="60" r="10" fill="none" stroke-width="2" stroke-dasharray="5 3" />
            <circle cx="150" cy="60" r="3" fill="#ffffff" />
          </g>
          <g class="car-wheel wheel-back">
            <circle cx="50" cy="60" r="10" fill="none" stroke-width="2" stroke-dasharray="5 3" />
            <circle cx="50" cy="60" r="3" fill="#ffffff" />
          </g>
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
  margin-top: 20px;
  overflow: visible;
}

.car-body {
  stroke: var(--color-primary);
  stroke-width: 2px;
  stroke-linecap: round;
  stroke-linejoin: round;
  filter: drop-shadow(0 0 4px rgba(220, 38, 38, 0.6));
}

.car-headlight {
  stroke: #ff3e3e;
  filter: drop-shadow(0 0 6px rgba(255, 62, 62, 0.8));
}

.car-chassis {
  animation: car-bounce 0.8s ease-in-out infinite alternate;
}

.car-wheel {
  stroke: #ffffff;
  filter: drop-shadow(0 0 3px rgba(255, 255, 255, 0.5));
  animation: wheel-spin 1.2s linear infinite;
}

.wheel-front {
  transform-origin: 150px 60px;
}

.wheel-back {
  transform-origin: 50px 60px;
}

.car-window {
  stroke: rgba(255, 255, 255, 0.35);
  stroke-width: 1.5px;
}

.car-window-divider {
  stroke: rgba(255, 255, 255, 0.35);
  stroke-width: 1.5px;
}

.car-taillight {
  stroke: #ff3e3e;
  filter: drop-shadow(0 0 4px rgba(255, 62, 62, 0.8));
}

.road-line {
  animation: road-slide 0.6s linear infinite;
}

/* Animations */
@keyframes car-bounce {
  0% {
    transform: translateY(0);
  }
  100% {
    transform: translateY(-1.5px);
  }
}

@keyframes wheel-spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

@keyframes road-slide {
  0% {
    stroke-dashoffset: 0;
  }
  100% {
    stroke-dashoffset: -14; /* Match stroke-dasharray (8 + 6 = 14) to loop seamlessly */
  }
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
