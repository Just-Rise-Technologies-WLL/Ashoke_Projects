<script setup>
import { RouterLink } from 'vue-router'
import { ArrowRight, PhoneCall } from 'lucide-vue-next'
</script>

<template>
  <section class="hero-section">
    <!-- Styled slate slate board pattern/gradient backdrop representing premium kitchen/dining (no image url) -->
    <div class="glow-backdrop"></div>
    <div class="herbs-svg-backdrop">
      <svg viewBox="0 0 100 100" class="leaf leaf-1">
        <path d="M10,50 Q30,40 50,50 Q30,60 10,50 Z" fill="rgba(0, 71, 27, 0.15)" stroke="rgba(0, 71, 27, 0.3)" stroke-width="1" />
        <line x1="10" y1="50" x2="50" y2="50" stroke="rgba(0, 71, 27, 0.3)" stroke-width="1" />
      </svg>
      <svg viewBox="0 0 100 100" class="leaf leaf-2">
        <path d="M10,50 Q30,40 50,50 Q30,60 10,50 Z" fill="rgba(0, 71, 27, 0.15)" stroke="rgba(0, 71, 27, 0.3)" stroke-width="1" />
        <line x1="10" y1="50" x2="50" y2="50" stroke="rgba(0, 71, 27, 0.3)" stroke-width="1" />
      </svg>
    </div>

    <div class="container hero-inner">
      <div class="hero-content animate-fade-in">
        <span class="hero-tag">PREMIUM MEAT TRADING FZCO</span>
        <h1 class="hero-title">
          Premium Quality<br>
          <span class="highlight">Fresh</span> Meat & Seafood
        </h1>
        <p class="hero-desc">
          Supplying the finest range of fresh halal meat, chicken, beef and seafood with an absolute commitment to quality, hygiene and customer satisfaction.
        </p>
        <div class="hero-actions">
          <RouterLink to="/products" class="btn btn-primary hero-btn">
            Our Products <ArrowRight size="16" />
          </RouterLink>
          <RouterLink to="/contact" class="btn btn-outline hero-btn">
            Contact Us <PhoneCall size="16" />
          </RouterLink>
        </div>
      </div>
      
      <!-- Visual Display: A stylized vector butcher board with knife and meat outline -->
      <div class="hero-graphic animate-fade-in">
        <div class="steak-display">
          <svg viewBox="0 0 160 160" class="steak-svg">
            <!-- Wooden Cutting Board -->
            <rect x="10" y="20" width="140" height="110" rx="8" fill="#5c4033" stroke="#3d2b22" stroke-width="3" />
            <rect x="20" y="30" width="120" height="90" rx="4" fill="none" stroke="#3d2b22" stroke-width="2" stroke-dasharray="4 2" />
            <rect x="5" y="65" width="10" height="20" rx="2" fill="#3d2b22" />
            
            <!-- Sleek Premium T-Bone Steak Vector -->
            <path d="M45,55 C65,40 105,45 115,65 C125,85 115,105 95,110 C75,115 55,105 45,95 C35,85 30,70 45,55 Z" fill="#b32000" stroke="#801000" stroke-width="3" />
            <!-- Meat Marbling (fat lines) -->
            <path d="M55,68 Q65,65 75,70" stroke="#ffebec" stroke-width="2" stroke-linecap="round" fill="none" />
            <path d="M65,85 Q78,82 88,90" stroke="#ffebec" stroke-width="2" stroke-linecap="round" fill="none" />
            <path d="M48,80 Q55,84 62,80" stroke="#ffebec" stroke-width="1.5" stroke-linecap="round" fill="none" />
            <!-- T-Bone -->
            <path d="M78,50 L78,92 L98,102 M78,72 L116,72" stroke="#ffebec" stroke-width="6" stroke-linecap="round" stroke-linejoin="round" fill="none" />
            <circle cx="78" cy="72" r="3" fill="#ffebec" />
          </svg>
        </div>
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

@media (min-width: 993px) {
  .hero-section {
    height: calc(100vh - 252px); /* 100vh - Header (80px) - Stats (100px approx) */
    min-height: 500px;
    padding: 0;
  }
}

.glow-backdrop {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: radial-gradient(circle at 80% 50%, rgba(0, 71, 27, 0.15) 0%, transparent 60%);
  pointer-events: none;
}

.herbs-svg-backdrop {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  pointer-events: none;
}

.leaf {
  position: absolute;
  width: 80px;
  height: 80px;
  filter: blur(1px);
}

.leaf-1 {
  top: 15%;
  right: 15%;
  transform: rotate(45deg);
}

.leaf-2 {
  bottom: 15%;
  right: 40%;
  transform: rotate(-30deg);
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
  display: inline-block;
  background-color: rgba(204, 41, 0, 0.1);
  border: 1px solid rgba(204, 41, 0, 0.3);
  color: var(--color-accent);
  padding: 6px 12px;
  border-radius: 50px;
  font-size: 11px;
  font-weight: 800;
  letter-spacing: 1px;
  margin-bottom: 24px;
}

.hero-title {
  font-size: 58px;
  font-weight: 900;
  line-height: 1.1;
  text-transform: uppercase;
  margin-bottom: 20px;
}

.hero-title .highlight {
  color: var(--color-accent);
}

.hero-desc {
  font-size: 17px;
  line-height: 1.7;
  color: var(--color-text-light);
  max-width: 540px;
  margin-bottom: 32px;
}

.hero-actions {
  display: flex;
  gap: 16px;
}

.hero-graphic {
  display: flex;
  justify-content: center;
  align-items: center;
}

.steak-display {
  width: 320px;
  height: 320px;
  position: relative;
  filter: drop-shadow(0 15px 30px rgba(0,0,0,0.5));
}

.steak-svg {
  width: 100%;
  height: 100%;
  animation: floatSteak 6s ease-in-out infinite;
}

@keyframes floatSteak {
  0%, 100% {
    transform: translateY(0) rotate(0deg);
  }
  50% {
    transform: translateY(-8px) rotate(2deg);
  }
}

@media (max-width: 992px) {
  .hero-inner {
    grid-template-columns: 1fr;
    text-align: center;
  }
  .hero-desc {
    margin-left: auto;
    margin-right: auto;
  }
  .hero-actions {
    justify-content: center;
  }
  .hero-graphic {
    margin-top: 40px;
    height: 260px;
  }
}

@media (max-width: 576px) {
  .hero-title {
    font-size: 40px;
  }
  .hero-actions {
    flex-direction: column;
    width: 100%;
  }
  .hero-actions .btn {
    width: 100%;
  }
}
</style>
