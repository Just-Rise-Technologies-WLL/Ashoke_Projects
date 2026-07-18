<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { ArrowRight, PhoneCall, HardHat, Wrench, Zap, Building } from 'lucide-vue-next'
import Button from '../ui/Button.vue'
import { isRequestModalOpen } from '@/composables/useModal'

const slides = [
  'https://images.unsplash.com/photo-1541888086425-d81bb19240f5?ixlib=rb-4.0.3&auto=format&fit=crop&w=2000&q=80',
  'https://images.unsplash.com/photo-1503387762-592deb58ef4e?ixlib=rb-4.0.3&auto=format&fit=crop&w=2000&q=80',
  'https://images.unsplash.com/photo-1508450859948-4e04fabaa4ea?ixlib=rb-4.0.3&auto=format&fit=crop&w=2000&q=80'
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
        v-for="(img, idx) in slides" 
        :key="idx" 
        class="slide-bg" 
        :class="{ active: currentSlide === idx }"
        :style="{ backgroundImage: `url(${img})` }"
      ></div>
    </div>
    
    <div class="hero-bg-overlay"></div>
    <div class="container hero-container">
      
      <div class="hero-content">
        <h3 class="hero-subtitle">YOUR TRUSTED</h3>
        <h1 class="hero-title">MANPOWER <br/>SUPPLY PARTNER<br/> <span class="highlight">IN UAE</span></h1>
        
        <p class="hero-desc">
          Providing skilled and semi-skilled workforce for construction, fit-out, MEP and building maintenance projects across UAE.
        </p>
        
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
          <Button to="tel:+971509390051" variant="outline" class="outline-action">
            <PhoneCall size="18" /> CALL NOW
          </Button>
        </div>
      </div>
      
    </div>
  </section>
</template>

<style scoped>
.hero-section {
  position: relative;
  min-height: 700px;
  display: flex;
  align-items: center;
  padding: 80px 0;
  overflow: hidden;
  background-color: #f4f6f4;
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
  font-size: 64px;
  color: #1a1e29; /* Dark shade matching the screenshot text */
  font-weight: 900;
  line-height: 1.1;
  margin-bottom: 24px;
}

.highlight {
  color: var(--color-primary); /* Matching "IN UAE" green */
}

.hero-desc {
  font-size: 18px;
  color: var(--color-text-main);
  max-width: 550px;
  margin-bottom: 40px;
  line-height: 1.6;
}

.hero-features {
  display: flex;
  flex-wrap: wrap;
  gap: 30px;
  margin-bottom: 50px;
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
</style>
