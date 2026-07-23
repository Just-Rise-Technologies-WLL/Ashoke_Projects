<script setup>
import { RouterLink } from 'vue-router'
import { ArrowRight, Wrench } from 'lucide-vue-next'
</script>

<template>
  <section class="hero-section">
    <div class="container hero-inner">
      
      <!-- Text Content -->
      <div class="hero-content animate-fade-in">
        <div class="hero-tag">
          <Wrench size="14" />
          <span>PREMIUM AUTO PARTS DISTRIBUTOR</span>
        </div>
        <h1 class="hero-title">
          Driving <span class="highlight">Quality</span>.<br>
          Delivering <span class="highlight">Trust</span>.
        </h1>
        <p class="hero-desc">
          Your trusted partner for high-quality, genuine, and aftermarket auto spare parts. We keep your fleet and personal vehicles moving with zero downtime.
        </p>
        <div class="hero-actions">
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
            <circle cx="50" cy="50" r="35" fill="none" stroke="#475569" stroke-width="6" />
            <path d="M50,10 L50,0 M60,12 L67,4 M70,16 L80,10 M78,22 L88,18 M84,30 L94,30 M86,38 L96,42 M85,47 L95,53 M82,56 L90,64 M76,64 L83,73 M68,71 L73,81 M60,76 L63,87 M50,78 L50,90 M40,76 L37,87 M32,71 L27,81 M24,64 L17,73 M18,56 L10,64 M15,47 L5,53 M14,38 L4,42 M16,30 L6,30 M22,22 L12,18 M30,16 L20,10 M40,12 L33,4" stroke="#475569" stroke-width="6" stroke-linecap="round" />
            <circle cx="50" cy="50" r="20" fill="#1e293b" stroke="#64748b" stroke-width="2" />
            <circle cx="50" cy="50" r="6" fill="#0f172a" />
          </svg>
        </div>
        <!-- Shadow backdrop glow -->
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

@media (min-width: 993px) {
  .hero-section {
    height: calc(100vh - 252px); /* 100vh - TopBar (37px) - Navbar (80px) - Features (135px approx) */
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

.hero-title {
  font-size: 58px;
  font-weight: 900;
  line-height: 1.1;
  text-transform: uppercase;
  margin-bottom: 20px;
}

.hero-title .highlight {
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
  background: radial-gradient(circle, rgba(220, 38, 38, 0.15) 0%, transparent 70%);
  z-index: 1;
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
