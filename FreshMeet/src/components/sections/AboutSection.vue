<script setup>
import { RouterLink } from 'vue-router'
import { Check, ArrowRight, ShieldCheck, Award } from 'lucide-vue-next'

const strengths = [
  'Strict quality control & hygiene',
  'Ethically sourced products',
  'Professional team & reliable service',
  'Customer satisfaction is our priority'
]
</script>

<template>
  <section class="about-section">
    <div class="container about-grid">
      
      <!-- Col 1: Text details -->
      <div class="about-info">
        <span class="section-subtitle">ABOUT OUR COMPANY</span>
        <h2 class="section-title text-left">Your Trusted Partner In <span>Quality Meat Supply</span></h2>
        <p class="about-desc">
          Fresh Cuts Meat Trading FZCO is a leading meat and seafood trading company in the UAE, committed to delivering premium quality products. We supply to supermarkets, restaurants, hotels, catering companies, and wholesalers across the region.
        </p>
        
        <ul class="strengths-list">
          <li v-for="str in strengths" :key="str" class="strength-item">
            <span class="chk-icon-box"><Check size="14" /></span>
            <span>{{ str }}</span>
          </li>
        </ul>
        
        <RouterLink to="/about" class="btn btn-primary about-btn">
          READ MORE ABOUT US <ArrowRight size="16" />
        </RouterLink>
      </div>
      
      <!-- Col 2: Center Photo Frame (Butcher Prepping Fresh Meat) -->
      <div class="about-graphic">
        <div class="photo-frame-box">
          <img 
            src="/images/butcher_prep_raw_meat.png" 
            alt="Fresh Cuts Butcher Prepping Quality Meat" 
            class="butcher-img"
          />
          <div class="logo-watermark-overlay">
            <span class="watermark-title">FRESH CUTS</span>
            <span class="watermark-sub">MEAT TRADING FZCO</span>
          </div>
        </div>
      </div>
      
      <!-- Col 3: Stat & Safety Badges matching UI design.jpeg -->
      <div class="about-badges">
        <div class="badge-card white-card">
          <div class="badge-header">
            <h3 class="experience-num">10+</h3>
            <div class="badge-text-group">
              <span class="exp-title">YEARS OF EXPERIENCE</span>
              <span class="exp-sub">Delivering Freshness Since 2014</span>
            </div>
          </div>
        </div>
        
        <div class="badge-card red-card">
          <div class="red-card-header">
            <ShieldCheck size="24" class="safety-icon" />
            <h3>COMMITTED TO QUALITY & SAFETY</h3>
          </div>
          <p class="red-card-desc">
            We follow international standards to ensure the best quality.
          </p>
        </div>
      </div>

    </div>
  </section>
</template>

<style scoped>
.about-section {
  background-color: #ffffff;
  padding: 80px 0;
}

.about-grid {
  display: grid;
  grid-template-columns: 1.2fr 1fr 0.9fr;
  gap: 36px;
  align-items: center;
}

.section-subtitle {
  color: #cc2900;
  font-size: 13px;
  font-weight: 800;
  letter-spacing: 1.5px;
  text-transform: uppercase;
  display: block;
  margin-bottom: 8px;
}

.section-title {
  font-size: 36px;
  font-weight: 900;
  color: #0f172a;
  line-height: 1.25;
  text-transform: uppercase;
  margin-bottom: 16px;
}

.section-title span {
  color: #cc2900;
}

.about-desc {
  font-size: 14px;
  line-height: 1.7;
  color: #64748b;
  margin-bottom: 24px;
}

.strengths-list {
  margin-bottom: 32px;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.strength-item {
  display: flex;
  align-items: center;
  gap: 12px;
  font-weight: 700;
  font-size: 13px;
  color: #1e293b;
}

.chk-icon-box {
  background-color: #cc2900;
  color: white;
  width: 22px;
  height: 22px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-shrink: 0;
}

.about-btn {
  background-color: #cc2900;
  color: white;
  padding: 14px 28px;
  font-weight: 800;
  font-size: 13px;
  border-radius: 4px;
  display: inline-flex;
  align-items: center;
  gap: 8px;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(204, 41, 0, 0.3);
}

.about-btn:hover {
  background-color: #e62e00;
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(204, 41, 0, 0.4);
}

/* Center Image Frame */
.about-graphic {
  display: flex;
  justify-content: center;
}

.photo-frame-box {
  position: relative;
  width: 100%;
  height: 380px;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.15);
}

.butcher-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.logo-watermark-overlay {
  position: absolute;
  top: 45%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
  background: rgba(12, 13, 14, 0.75);
  padding: 12px 24px;
  border-radius: 8px;
  border: 1px solid rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(4px);
}

.watermark-title {
  display: block;
  color: white;
  font-weight: 900;
  font-size: 18px;
  letter-spacing: 1px;
}

.watermark-sub {
  display: block;
  color: #ff4d2d;
  font-size: 10px;
  font-weight: 800;
  letter-spacing: 0.5px;
}

/* Col 3 Badges matching UI design.jpeg */
.about-badges {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.badge-card {
  border-radius: 10px;
  padding: 24px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
}

.white-card {
  background-color: #ffffff;
  border: 1px solid #e2e8f0;
}

.badge-header {
  display: flex;
  align-items: center;
  gap: 16px;
}

.experience-num {
  font-size: 42px;
  font-weight: 900;
  color: #cc2900;
  line-height: 1;
}

.badge-text-group {
  display: flex;
  flex-direction: column;
}

.exp-title {
  font-weight: 900;
  font-size: 13px;
  color: #0f172a;
  letter-spacing: 0.5px;
}

.exp-sub {
  font-size: 12px;
  color: #64748b;
  margin-top: 4px;
}

.red-card {
  background-color: #cc2900;
  color: white;
}

.red-card-header {
  display: flex;
  align-items: flex-start;
  gap: 12px;
  margin-bottom: 10px;
}

.safety-icon {
  color: white;
  flex-shrink: 0;
}

.red-card-header h3 {
  font-size: 14px;
  font-weight: 900;
  letter-spacing: 0.5px;
  line-height: 1.3;
  margin: 0;
}

.red-card-desc {
  font-size: 12px;
  line-height: 1.6;
  color: rgba(255, 255, 255, 0.9);
  margin: 0;
}

@media (max-width: 992px) {
  .about-grid {
    grid-template-columns: 1fr;
  }
  .about-graphic {
    order: -1;
  }
}
</style>

