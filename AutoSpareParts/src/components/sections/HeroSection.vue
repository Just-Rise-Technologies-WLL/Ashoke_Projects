<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { RouterLink } from 'vue-router'
import { ArrowRight, Wrench } from 'lucide-vue-next'

const currentSlide = ref(0)
let slideTimer = null

const slides = [
  {
    title: 'Driving <span class="highlight">Quality</span>.<br>Delivering <span class="highlight">Trust</span>.',
    desc: 'Your trusted partner for high-quality, genuine, and aftermarket auto spare parts. We keep your fleet and personal vehicles moving with zero downtime.',
    image: '/images/hero/slide1.jpg'
  },
  {
    title: 'Precision <span class="highlight">Fitment</span>.<br>Absolute <span class="highlight">Safety</span>.',
    desc: 'Sourcing directly from verified global manufacturers to guarantee exact compatibility, durability, and ultimate road security.',
    image: '/images/hero/slide2.jpg'
  },
  {
    title: 'Global <span class="highlight">Logistics</span>.<br>Prompt <span class="highlight">Delivery</span>.',
    desc: 'Operating out of our Al Quoz logistics hub in Dubai to dispatch orders swiftly across the GCC with zero delays.',
    image: '/images/hero/slide3.jpg'
  }
]

onMounted(() => {
  slideTimer = setInterval(() => {
    currentSlide.value = (currentSlide.value + 1) % slides.length
  }, 5000)
})

onUnmounted(() => {
  if (slideTimer) clearInterval(slideTimer)
})
</script>

<template>
  <!-- Main section with dynamic background image transition -->
  <section class="hero-section">
    <!-- Slide Backgrounds for smooth crossfade transition -->
    <div 
      v-for="(slide, index) in slides" 
      :key="index"
      class="hero-slide-bg"
      :class="{ active: index === currentSlide }"
      :style="{ backgroundImage: 'linear-gradient(rgba(10, 11, 13, 0.82), rgba(10, 11, 13, 0.88)), url(' + slide.image + ')' }"
    ></div>

    <!-- High-tech grid backdrop overlay -->
    <div class="grid-overlay"></div>
    
    <div class="container hero-inner">
      
      <!-- Text Content with Transition -->
      <div class="hero-content">
        <div class="hero-tag animate-fade-in">
          <Wrench size="14" />
          <span>PREMIUM AUTO PARTS DISTRIBUTOR</span>
        </div>
        
        <Transition name="slide-fade" mode="out-in">
          <div :key="currentSlide" class="slide-content-wrapper">
            <h1 class="hero-title" v-html="slides[currentSlide].title"></h1>
            <p class="hero-desc">{{ slides[currentSlide].desc }}</p>
          </div>
        </Transition>

        <div class="hero-actions animate-fade-in">
          <RouterLink to="/products" class="btn btn-primary hero-btn">
            Shop Now <ArrowRight size="16" />
          </RouterLink>
        </div>
      </div>
      
      <!-- Styled Auto Parts Illustration / Backdrop Graphic -->
      <div class="hero-graphic animate-fade-in">
        <div class="parts-showcase">
          <!-- Brake Disc SVG -->
          <svg viewBox="0 0 100 100" class="showcase-svg rotor">
            <circle cx="50" cy="50" r="45" fill="none" stroke="#334155" stroke-width="6" />
            <circle cx="50" cy="50" r="30" fill="none" stroke="#475569" stroke-width="2" stroke-dasharray="2 3" />
            <circle cx="50" cy="50" r="20" fill="#1e293b" stroke="#64748b" stroke-width="2" />
            <rect x="47" y="10" width="6" height="80" fill="none" stroke="#64748b" stroke-width="1.5" transform="rotate(45 50 50)" />
            <rect x="47" y="10" width="6" height="80" fill="none" stroke="#64748b" stroke-width="1.5" transform="rotate(135 50 50)" />
            <circle cx="50" cy="50" r="8" fill="#0f172a" />
            <!-- Red Brake Caliper Overlay -->
            <path d="M72,18 C85,30 85,50 78,65 L88,60 C94,44 92,26 80,12 Z" fill="#dc2626" />
          </svg>
          
          <!-- Gear SVG -->
          <svg viewBox="0 0 100 100" class="showcase-svg gear">
            <circle cx="50" cy="50" r="28" fill="none" stroke="#475569" stroke-width="6" />
            <g fill="#475569">
              <rect x="47" y="12" width="6" height="10" rx="1.5" transform="rotate(0 50 50)" />
              <rect x="47" y="12" width="6" height="10" rx="1.5" transform="rotate(30 50 50)" />
              <rect x="47" y="12" width="6" height="10" rx="1.5" transform="rotate(60 50 50)" />
              <rect x="47" y="12" width="6" height="10" rx="1.5" transform="rotate(90 50 50)" />
              <rect x="47" y="12" width="6" height="10" rx="1.5" transform="rotate(120 50 50)" />
              <rect x="47" y="12" width="6" height="10" rx="1.5" transform="rotate(150 50 50)" />
              <rect x="47" y="12" width="6" height="10" rx="1.5" transform="rotate(180 50 50)" />
              <rect x="47" y="12" width="6" height="10" rx="1.5" transform="rotate(210 50 50)" />
              <rect x="47" y="12" width="6" height="10" rx="1.5" transform="rotate(240 50 50)" />
              <rect x="47" y="12" width="6" height="10" rx="1.5" transform="rotate(270 50 50)" />
              <rect x="47" y="12" width="6" height="10" rx="1.5" transform="rotate(300 50 50)" />
              <rect x="47" y="12" width="6" height="10" rx="1.5" transform="rotate(330 50 50)" />
            </g>
            <circle cx="50" cy="50" r="18" fill="#1e293b" stroke="#64748b" stroke-width="2" />
            <circle cx="50" cy="50" r="6" fill="#0f172a" />
          </svg>
        </div>
        <!-- Dynamic Glow background -->
        <div class="glow-backdrop"></div>
      </div>

    </div>
  </section>
</template>

<style scoped>
.hero-section {
  background-color: var(--color-dark);
  color: white;
  min-height: 580px;
  display: flex;
  align-items: center;
  position: relative;
  overflow: hidden;
  padding: 60px 0;
}

.hero-slide-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  opacity: 0;
  transition: opacity 1.2s ease-in-out;
  z-index: 1;
}

.hero-slide-bg.active {
  opacity: 1;
}

.grid-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: linear-gradient(rgba(255, 255, 255, 0.015) 1px, transparent 1px),
                    linear-gradient(90deg, rgba(255, 255, 255, 0.015) 1px, transparent 1px);
  background-size: 40px 40px;
  pointer-events: none;
  z-index: 2;
}

@media (min-width: 993px) {
  .hero-section {
    height: calc(100vh - 252px);
    min-height: 500px;
    padding: 0;
  }
}

.hero-inner {
  display: grid;
  grid-template-columns: 1.2fr 0.8fr;
  gap: 40px;
  align-items: center;
  position: relative;
  z-index: 10;
}

.hero-tag {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background-color: rgba(220, 38, 38, 0.15);
  border: 1px solid rgba(220, 38, 38, 0.3);
  color: var(--color-primary);
  padding: 6px 12px;
  border-radius: 50px;
  font-size: 11px;
  font-weight: 800;
  letter-spacing: 1px;
  margin-bottom: 24px;
}

.slide-content-wrapper {
  min-height: 250px;
}

.hero-title {
  font-size: 58px;
  font-weight: 900;
  line-height: 1.1;
  text-transform: uppercase;
  margin-bottom: 20px;
}

:deep(.hero-title .highlight) {
  color: var(--color-primary);
}

.hero-desc {
  font-size: 17px;
  line-height: 1.7;
  color: var(--color-text-light);
  max-width: 540px;
  margin-bottom: 32px;
}

.hero-graphic {
  position: relative;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.parts-showcase {
  position: relative;
  width: 320px;
  height: 320px;
  z-index: 10;
}

.showcase-svg {
  position: absolute;
  filter: drop-shadow(0 10px 20px rgba(0,0,0,0.5));
  transition: transform 0.5s ease;
}

.showcase-svg.rotor {
  width: 260px;
  height: 260px;
  top: 0;
  right: 0;
  animation: floatRotor 6s ease-in-out infinite;
}

.showcase-svg.gear {
  width: 140px;
  height: 140px;
  bottom: 0;
  left: 0;
  animation: spinGear 12s linear infinite;
}

.glow-backdrop {
  position: absolute;
  width: 300px;
  height: 300px;
  background: radial-gradient(circle, rgba(220, 38, 38, 0.1) 0%, transparent 70%);
  z-index: 1;
}

/* Slide Transition Animations */
.slide-fade-enter-active,
.slide-fade-leave-active {
  transition: all 0.6s cubic-bezier(0.4, 0, 0.2, 1);
}

.slide-fade-enter-from {
  opacity: 0;
  transform: translateX(15px);
}

.slide-fade-leave-to {
  opacity: 0;
  transform: translateX(-15px);
}

@keyframes floatRotor {
  0%, 100% {
    transform: translateY(0) rotate(0deg);
  }
  50% {
    transform: translateY(-10px) rotate(5deg);
  }
}

@keyframes spinGear {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(-360deg);
  }
}

@media (max-width: 992px) {
  .hero-inner {
    grid-template-columns: 1fr;
    text-align: center;
  }
  
  .hero-tag {
    justify-content: center;
  }
  
  .slide-content-wrapper {
    min-height: 200px;
  }

  .hero-desc {
    margin-left: auto;
    margin-right: auto;
  }
  
  .hero-actions {
    justify-content: center;
    display: flex;
  }
  
  .hero-graphic {
    margin-top: 40px;
    height: 300px;
  }
}

@media (max-width: 576px) {
  .hero-title {
    font-size: 42px;
  }
}
</style>
