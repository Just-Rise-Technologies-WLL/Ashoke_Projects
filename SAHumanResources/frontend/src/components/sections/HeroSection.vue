<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { ArrowRight, PhoneCall, HardHat, Wrench, Zap, Building } from 'lucide-vue-next'
import Button from '../ui/Button.vue'
import { isRequestModalOpen } from '@/composables/useModal'

const slides = [
  {
    image: '/images/hero1.jpg',
    subtitle: 'YOUR TRUSTED',
    title: 'MANPOWER <br/>SUPPLY PARTNER<br/> <span class="highlight">IN UAE</span>',
    desc: 'Providing skilled and semi-skilled workforce for construction, fit-out, MEP and building maintenance projects across UAE.'
  },
  {
    image: '/images/hero2.jpg',
    subtitle: 'EXPERT MEP & FIT-OUT',
    title: 'SKILLED WORKFORCE<br/> <span class="highlight">ON DEMAND</span>',
    desc: 'Empowering your projects with experienced electrical, plumbing, and interior fit-out professionals.'
  },
  {
    image: '/images/hero3.jpg',
    subtitle: 'CONSTRUCTION LEADERS',
    title: 'RELIABLE BUILDERS<br/> <span class="highlight">IN DUBAI</span>',
    desc: 'Certified professionals dedicated to maintaining the highest safety and building construction standards.'
  }
]

const currentSlide = ref(0)
let slideInterval

onMounted(() => {
  slideInterval = setInterval(() => {
    currentSlide.value = (currentSlide.value + 1) % slides.length
  }, 5000)
})

onUnmounted(() => {
  clearInterval(slideInterval)
})

const openModal = () => {
  isRequestModalOpen.value = true
}
</script>

<template>
  <section class="hero-section">
    
    <!-- Background Slider -->
    <div class="hero-slider">
      <div 
        v-for="(slide, idx) in slides" 
        :key="idx" 
        class="slide-bg" 
        :class="{ active: currentSlide === idx }"
        :style="{ backgroundImage: `url(${slide.image})` }"
      ></div>
    </div>
    
    <div class="hero-bg-overlay"></div>
    <div class="container hero-container">
      
      <div class="hero-content">
        <Transition name="text-slide" mode="out-in">
          <div :key="currentSlide">
            <h3 class="hero-subtitle">{{ slides[currentSlide].subtitle }}</h3>
            <h1 class="hero-title" v-html="slides[currentSlide].title"></h1>
            
            <p class="hero-desc">
              {{ slides[currentSlide].desc }}
            </p>
          </div>
        </Transition>
        
        <div class="hero-features">
          <div class="feature"><HardHat size="24" class="feature-icon" /> <span>Construction</span></div>
          <div class="feature"><Wrench size="24" class="feature-icon" /> <span>Fit Out</span></div>
          <div class="feature"><Zap size="24" class="feature-icon" /> <span>MEP</span></div>
          <div class="feature"><Building size="24" class="feature-icon" /> <span>Building Maintenance</span></div>
        </div>
        
        <div class="hero-actions">
          <Button @click="openModal" variant="primary" class="primary-action">
             REQUEST MANPOWER <ArrowRight size="18" />
          </Button>
          <Button to="tel:+971589390051" variant="outline" class="outline-action">
            <PhoneCall size="18" /> CALL NOW
          </Button>
        </div>
      </div>
      
      <!-- Floating MOHRE Compliant trust badge -->
      <div class="mohre-badge-wrapper">
        <div class="mohre-badge">
          <div class="mohre-badge-inner">
            <div class="shield-icon-box">
              <svg viewBox="0 0 24 24" width="28" height="28" fill="none" stroke="#4caf50" stroke-width="2.5" class="shield-svg">
                <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z" />
                <path d="M9 11l2 2 4-4" stroke-linecap="round" stroke-linejoin="round" />
              </svg>
            </div>
            <div class="mohre-text">
              <span class="mohre-title">MOHRE</span>
              <span class="mohre-subtitle">COMPLIANT</span>
            </div>
          </div>
        </div>
      </div>
      
    </div>
  </section>
</template>

<style scoped>
.hero-section {
  position: relative;
  min-height: 540px;
  display: flex;
  align-items: center;
  padding: 40px 0;
  overflow: hidden;
  background-color: #f4f6f4;
}

/* Floating MOHRE badge styling */
.mohre-badge-wrapper {
  position: absolute;
  right: 60px;
  bottom: 80px;
  z-index: 5;
  animation: pulseBadge 3s ease-in-out infinite;
}

.mohre-badge {
  background: white;
  padding: 16px 28px;
  border-radius: 16px;
  box-shadow: 0 15px 35px rgba(0, 71, 27, 0.12);
  border: 1px solid rgba(0, 71, 27, 0.05);
}

.mohre-badge-inner {
  display: flex;
  align-items: center;
  gap: 16px;
}

.shield-icon-box {
  display: flex;
  align-items: center;
  justify-content: center;
}

.mohre-text {
  display: flex;
  flex-direction: column;
}

.mohre-title {
  font-size: 22px;
  font-weight: 900;
  color: #00471b;
  line-height: 1.1;
  letter-spacing: 0.5px;
}

.mohre-subtitle {
  font-size: 11px;
  font-weight: 700;
  color: #757575;
  letter-spacing: 1px;
}

@keyframes pulseBadge {
  0%, 100% {
    transform: translateY(0) scale(1);
  }
  50% {
    transform: translateY(-5px) scale(1.02);
  }
}

@media (max-width: 992px) {
  .mohre-badge-wrapper {
    position: static;
    display: flex;
    justify-content: center;
    margin-top: 30px;
    width: 100%;
    animation: none;
  }
  .mohre-badge {
    padding: 12px 20px;
  }
  .mohre-title {
    font-size: 18px;
  }
}

@media (min-width: 993px) {
  .hero-section {
    height: calc(100vh - 252px);
    min-height: 500px;
    padding: 0;
  }
}

/* Background Slider Architecture */
.hero-slider {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 0;
}

.slide-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center right;
  background-repeat: no-repeat;
  opacity: 0;
  transition: opacity 1.2s ease-in-out;
}

.slide-bg.active {
  opacity: 1;
}

/* Gradient overlay to ensure the left-side text remains perfectly legible over the background image */
.hero-bg-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(to right, rgba(255, 255, 255, 1) 0%, rgba(255, 255, 255, 0.95) 45%, rgba(255, 255, 255, 0) 80%);
  z-index: 1;
}

.hero-container {
  position: relative;
  z-index: 2;
  width: 100%;
}

.hero-content {
  max-width: 650px;
}

.hero-subtitle {
  color: var(--color-primary);
  font-weight: 800;
  font-size: 20px;
  letter-spacing: 1px;
  margin-bottom: 5px;
}

.hero-title {
  font-size: 52px;
  color: #1a1e29; /* Dark shade matching the screenshot text */
  font-weight: 900;
  line-height: 1.1;
  margin-bottom: 16px;
}

:deep(.highlight) {
  color: var(--color-primary); /* Matching "IN UAE" green */
}

.hero-desc {
  font-size: 18px;
  color: var(--color-text-main);
  max-width: 550px;
  margin-bottom: 24px;
  line-height: 1.6;
}

.hero-features {
  display: flex;
  flex-wrap: wrap;
  gap: 30px;
  margin-bottom: 30px;
}

.feature {
  display: flex;
  align-items: center;
  gap: 10px;
  font-weight: 700;
  font-size: 14px;
  color: var(--color-text-main);
}

.feature-icon {
  color: var(--color-accent);
}

.hero-actions {
  display: flex;
  gap: 20px;
  flex-wrap: wrap;
}

.primary-action {
  font-weight: 800;
  padding: 16px 32px;
}

.outline-action {
  font-weight: 800;
  border: 2px solid var(--color-primary);
  color: var(--color-primary);
  background-color: white;
  padding: 16px 32px;
}
.outline-action:hover {
  background-color: var(--color-primary);
  color: white;
}

@media (max-width: 992px) {
  .hero-section {
    min-height: 600px;
  }
  .slide-bg {
    background-position: center; 
  }
  .hero-bg-overlay {
    background: linear-gradient(to bottom, rgba(255, 255, 255, 0.95) 0%, rgba(255, 255, 255, 0.9) 60%, rgba(255, 255, 255, 0.3) 100%);
  }
  .hero-content {
    text-align: center;
    margin: 0 auto;
  }
  .hero-desc {
    margin: 0 auto 30px auto;
  }
  .hero-features {
    justify-content: center;
  }
  .hero-actions {
    justify-content: center;
  }
  .hero-title {
    font-size: 48px;
  }
}

@media (max-width: 576px) {
  .hero-title {
    font-size: 40px;
  }
  .hero-features {
    gap: 15px;
  }
  .hero-actions {
    flex-direction: column;
    width: 100%;
  }
  .hero-actions > * {
    width: 100%;
  }
}

/* Text Transition */
.text-slide-enter-active,
.text-slide-leave-active {
  transition: all 0.6s cubic-bezier(0.4, 0, 0.2, 1);
}

.text-slide-enter-from {
  opacity: 0;
  transform: translateY(20px);
}

.text-slide-leave-to {
  opacity: 0;
  transform: translateY(-20px);
}
</style>
