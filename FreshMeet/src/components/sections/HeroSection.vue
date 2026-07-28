<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { RouterLink } from 'vue-router'
import { ArrowRight, PhoneCall, ChevronLeft, ChevronRight, ShieldCheck, Moon, Snowflake, Award } from 'lucide-vue-next'

const slides = ref([
  {
    id: 1,
    tag: 'PREMIUM MEAT TRADING FZCO',
    title: 'PREMIUM QUALITY',
    titleHighlight: 'FRESH MEAT & SEAFOOD',
    description: 'Supplying the finest range of fresh raw beef, chicken, lamb and seafood with an absolute commitment to quality, hygiene and customer satisfaction.',
    bgImage: '/images/raw_beef_steak.png',
    image: '/images/raw_beef_steak.png',
    badge: '100% Fresh Halal Raw Beef'
  },
  {
    id: 2,
    tag: 'FARM FRESH POULTRY',
    title: 'HYGIENIC & TENDER',
    titleHighlight: 'FRESH RAW CHICKEN',
    description: 'Directly sourced farm-fresh raw poultry processed under strict temperature-controlled sanitary standards for restaurants & wholesale.',
    bgImage: '/images/raw_farm_chicken.png',
    image: '/images/raw_farm_chicken.png',
    badge: 'Hygienic Raw Farm Chicken'
  },
  {
    id: 3,
    tag: 'OCEAN FRESH CATCH',
    title: 'WILD & SUSTAINABLE',
    titleHighlight: 'FRESH RAW SEAFOOD',
    description: 'Daily fresh catch prawns, raw salmon fillets, and white fish delivered in ice-cold chain logistics to preserve peak natural flavor.',
    bgImage: '/images/raw_fresh_seafood.png',
    image: '/images/raw_fresh_seafood.png',
    badge: 'Daily Fresh Raw Catch'
  },
  {
    id: 4,
    tag: 'ORGANIC LAMB & MUTTON',
    title: 'JUICY & TENDER',
    titleHighlight: 'RAW LAMB CHOPS',
    description: 'Choice cuts of raw grass-fed lamb and mutton, perfect for high-end dining establishments, hotels, and retail meat markets.',
    bgImage: '/images/raw_lamb_chops.png',
    image: '/images/raw_lamb_chops.png',
    badge: 'Grass-Fed Raw Prime Lamb'
  }
])

const currentSlide = ref(0)
let timer = null

const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % slides.value.length
}

const prevSlide = () => {
  currentSlide.value = (currentSlide.value - 1 + slides.value.length) % slides.value.length
}

const goToSlide = (index) => {
  currentSlide.value = index
}

const startTimer = () => {
  stopTimer()
  timer = setInterval(nextSlide, 6000)
}

const stopTimer = () => {
  if (timer) clearInterval(timer)
}

onMounted(() => {
  startTimer()
})

onUnmounted(() => {
  stopTimer()
})
</script>

<template>
  <section class="hero-section" @mouseenter="stopTimer" @mouseleave="startTimer">
    <!-- Background Image Slides with Smooth Fade -->
    <div class="slider-bg-container">
      <div 
        v-for="(slide, index) in slides" 
        :key="'bg-' + slide.id" 
        class="slide-bg"
        :class="{ active: currentSlide === index }"
        :style="{ backgroundImage: `linear-gradient(to right, rgba(12, 13, 14, 0.95) 40%, rgba(12, 13, 14, 0.65) 75%, rgba(12, 13, 14, 0.9) 100%), url(${slide.bgImage})` }"
      ></div>
    </div>

    <!-- Navigation Overlay Arrows -->
    <button @click="prevSlide" aria-label="Previous slide" class="slider-arrow prev-arrow">
      <ChevronLeft size="24" />
    </button>
    <button @click="nextSlide" aria-label="Next slide" class="slider-arrow next-arrow">
      <ChevronRight size="24" />
    </button>

    <div class="container hero-inner">
      <!-- Main Content Text per Slide -->
      <div 
        v-for="(slide, index) in slides" 
        :key="'content-' + slide.id" 
        class="hero-content"
        :class="{ active: currentSlide === index }"
      >
        <div class="tag-wrap">
          <span class="hero-tag slide-animated-item delay-1">{{ slide.tag }}</span>
        </div>
        <h1 class="hero-title slide-animated-item delay-2">
          {{ slide.title }}<br>
          <span class="highlight">{{ slide.titleHighlight }}</span>
        </h1>
        <p class="hero-desc slide-animated-item delay-3">
          {{ slide.description }}
        </p>
        <div class="hero-actions slide-animated-item delay-4">
          <RouterLink to="/products" class="btn btn-primary hero-btn">
            OUR PRODUCTS <ArrowRight size="16" />
          </RouterLink>
          <RouterLink to="/contact" class="btn btn-outline hero-btn">
            CONTACT US <PhoneCall size="16" />
          </RouterLink>
        </div>

        <!-- Slide Dots cleanly positioned under buttons -->
        <div class="slider-dots inline-dots">
          <button 
            v-for="(s, idx) in slides" 
            :key="'dot-' + s.id"
            @click="goToSlide(idx)" 
            class="dot"
            :class="{ active: currentSlide === idx }"
            :aria-label="'Go to slide ' + (idx + 1)"
          ></button>
        </div>
      </div>
      
      <!-- Right Graphic / Image Display per Slide -->
      <div class="hero-graphic">
        <div 
          v-for="(slide, index) in slides" 
          :key="'image-' + slide.id"
          class="image-frame-wrap"
          :class="{ active: currentSlide === index }"
        >
          <div class="glow-ring"></div>
          <img :src="slide.image" :alt="slide.title" class="featured-meat-img" />
          <div class="floating-badge">
            <span>{{ slide.badge }}</span>
          </div>
        </div>
      </div>
    </div>

    <!-- Features Bar matching UI design.jpeg -->
    <div class="features-bar">
      <div class="container features-bar-grid">
        <div class="feature-item">
          <div class="feature-icon-box">
            <ShieldCheck size="24" />
          </div>
          <div class="feature-text">
            <h4>100% FRESH</h4>
            <p>Always Fresh, Never Frozen</p>
          </div>
        </div>

        <div class="feature-item">
          <div class="feature-icon-box">
            <Moon size="24" />
          </div>
          <div class="feature-text">
            <h4>HALAL CERTIFIED</h4>
            <p>Halal & Hygienic Process</p>
          </div>
        </div>

        <div class="feature-item">
          <div class="feature-icon-box">
            <Snowflake size="24" />
          </div>
          <div class="feature-text">
            <h4>COLD CHAIN DELIVERY</h4>
            <p>Maintained Freshness</p>
          </div>
        </div>

        <div class="feature-item">
          <div class="feature-icon-box">
            <Award size="24" />
          </div>
          <div class="feature-text">
            <h4>BEST QUALITY</h4>
            <p>Premium & Trusted</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero-section {
  background-color: #0c0d0e;
  color: white;
  min-height: 600px;
  position: relative;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding-top: 20px;
}

@media (min-width: 993px) {
  .hero-section {
    min-height: calc(100vh - 80px);
    padding-top: 30px;
  }
}

/* Background Slider */
.slider-bg-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
}

.slide-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
  opacity: 0;
  transition: opacity 1.2s cubic-bezier(0.4, 0, 0.2, 1);
  transform: scale(1.05);
}

.slide-bg.active {
  opacity: 1;
  transform: scale(1);
  transition: opacity 1.2s cubic-bezier(0.4, 0, 0.2, 1), transform 6s ease-out;
}

.hero-inner {
  display: grid;
  grid-template-columns: 1.1fr 0.9fr;
  gap: 40px;
  align-items: center;
  position: relative;
  z-index: 10;
  padding-top: 30px;
  padding-bottom: 40px;
  margin-top: auto;
  margin-bottom: auto;
}

/* Hero Content Stack */
.hero-content {
  display: none;
}

.hero-content.active {
  display: block;
}

.tag-wrap {
  margin-bottom: 16px;
  padding-top: 10px;
}

.hero-tag {
  display: inline-block;
  background-color: rgba(204, 41, 0, 0.2);
  border: 1px solid rgba(204, 41, 0, 0.5);
  color: #ff4d2d;
  padding: 6px 14px;
  border-radius: 50px;
  font-size: 11px;
  font-weight: 800;
  letter-spacing: 1.5px;
  text-transform: uppercase;
}

.hero-title {
  font-size: 52px;
  font-weight: 900;
  line-height: 1.1;
  text-transform: uppercase;
  margin-bottom: 20px;
  letter-spacing: -0.5px;
}

.hero-title .highlight {
  color: #cc2900;
  background: linear-gradient(135deg, #ff4d2d 0%, #cc2900 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.hero-desc {
  font-size: 16px;
  line-height: 1.7;
  color: #d1d5db;
  max-width: 520px;
  margin-bottom: 32px;
}

.hero-actions {
  display: flex;
  gap: 16px;
  margin-bottom: 28px;
}

.hero-btn {
  padding: 14px 28px;
  font-weight: 800;
  font-size: 13px;
  letter-spacing: 1px;
  text-transform: uppercase;
  border-radius: 4px;
  display: inline-flex;
  align-items: center;
  gap: 8px;
  transition: all 0.3s ease;
}

.btn-primary {
  background-color: #cc2900;
  color: white;
  border: none;
  box-shadow: 0 8px 20px rgba(204, 41, 0, 0.4);
}

.btn-primary:hover {
  background-color: #e62e00;
  transform: translateY(-2px);
  box-shadow: 0 12px 25px rgba(204, 41, 0, 0.5);
}

.btn-outline {
  background: rgba(255, 255, 255, 0.05);
  color: white;
  border: 1px solid rgba(255, 255, 255, 0.3);
  backdrop-filter: blur(5px);
}

.btn-outline:hover {
  background: white;
  color: #0c0d0e;
  border-color: white;
  transform: translateY(-2px);
}

/* Animations for Slide Elements */
.hero-content.active .slide-animated-item {
  animation: slideUpFade 0.8s cubic-bezier(0.16, 1, 0.3, 1) forwards;
}

.delay-1 { animation-delay: 0.1s; opacity: 0; }
.delay-2 { animation-delay: 0.25s; opacity: 0; }
.delay-3 { animation-delay: 0.4s; opacity: 0; }
.delay-4 { animation-delay: 0.55s; opacity: 0; }

@keyframes slideUpFade {
  from {
    opacity: 0;
    transform: translateY(24px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Right Graphic Frame */
.hero-graphic {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}

.image-frame-wrap {
  display: none;
  position: relative;
  width: 100%;
  max-width: 440px;
  height: 360px;
}

.image-frame-wrap.active {
  display: flex;
  justify-content: center;
  align-items: center;
  animation: zoomFade 0.9s cubic-bezier(0.16, 1, 0.3, 1) forwards;
}

@keyframes zoomFade {
  from {
    opacity: 0;
    transform: scale(0.92);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}

.glow-ring {
  position: absolute;
  width: 320px;
  height: 320px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(204, 41, 0, 0.35) 0%, transparent 70%);
  filter: blur(25px);
  z-index: 1;
}

.featured-meat-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 16px;
  border: 2px solid rgba(255, 255, 255, 0.15);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.6);
  position: relative;
  z-index: 2;
}

.floating-badge {
  position: absolute;
  bottom: -15px;
  right: 15px;
  background: rgba(12, 13, 14, 0.9);
  border: 1px solid rgba(204, 41, 0, 0.6);
  color: white;
  padding: 8px 18px;
  border-radius: 30px;
  font-size: 12px;
  font-weight: 800;
  letter-spacing: 0.5px;
  z-index: 3;
  backdrop-filter: blur(10px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.4);
}

/* Arrows & Dots Controls */
.slider-arrow {
  position: absolute;
  top: 42%;
  transform: translateY(-50%);
  z-index: 20;
  background: rgba(12, 13, 14, 0.6);
  border: 1px solid rgba(255, 255, 255, 0.2);
  color: white;
  width: 44px;
  height: 44px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.3s ease;
  backdrop-filter: blur(4px);
}

.slider-arrow:hover {
  background: #cc2900;
  border-color: #cc2900;
  transform: translateY(-50%) scale(1.1);
}

.prev-arrow { left: 20px; }
.next-arrow { right: 20px; }

.inline-dots {
  display: flex;
  gap: 10px;
  z-index: 20;
}

.dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.3);
  border: none;
  cursor: pointer;
  transition: all 0.3s ease;
}

.dot.active {
  width: 32px;
  border-radius: 10px;
  background: #cc2900;
}

/* Features Bar directly integrated matching UI design.jpeg */
.features-bar {
  position: relative;
  z-index: 15;
  background: rgba(18, 19, 21, 0.95);
  border-top: 1px solid rgba(255, 255, 255, 0.08);
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
  padding: 22px 0;
  backdrop-filter: blur(10px);
}

.features-bar-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
}

.feature-item {
  display: flex;
  align-items: center;
  gap: 14px;
  padding: 6px 12px;
}

.feature-icon-box {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  background: rgba(204, 41, 0, 0.15);
  border: 1px solid rgba(204, 41, 0, 0.3);
  color: #ff4d2d;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.feature-text h4 {
  font-size: 13px;
  font-weight: 800;
  letter-spacing: 0.5px;
  color: white;
  margin: 0 0 2px 0;
  text-transform: uppercase;
}

.feature-text p {
  font-size: 12px;
  color: #9ca3af;
  margin: 0;
}

@media (max-width: 992px) {
  .hero-inner {
    grid-template-columns: 1fr;
    text-align: center;
    padding-bottom: 30px;
  }
  .hero-desc {
    margin-left: auto;
    margin-right: auto;
  }
  .hero-actions {
    justify-content: center;
  }
  .inline-dots {
    justify-content: center;
  }
  .image-frame-wrap {
    height: 280px;
    margin: 20px auto 0;
  }
  .features-bar-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 24px;
  }
  .slider-arrow { display: none; }
}

@media (max-width: 576px) {
  .hero-title {
    font-size: 34px;
  }
  .hero-actions {
    flex-direction: column;
  }
  .hero-btn {
    width: 100%;
    justify-content: center;
  }
  .features-bar-grid {
    grid-template-columns: 1fr;
  }
}
</style>


