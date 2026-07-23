<script setup>
import { RouterLink } from 'vue-router'
import { Check, ArrowRight, Award, ShieldAlert } from 'lucide-vue-next'

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
        <span class="section-subtitle">About Our Company</span>
        <h2 class="section-title text-left">Your Trusted Partner In <span>Meat Supply</span></h2>
        <p class="about-desc">
          Fresh Cuts Meat Trading FZCO is a leading supplier of fresh, premium-grade meat and seafood across the United Arab Emirates. We are committed to maintaining the highest sanitation standards in the industry.
        </p>
        <p class="about-desc">
          We operate a temperature-controlled cold chain network that ensures all meats retain their texture, freshness, and nutritive values from selection to delivery.
        </p>
        
        <ul class="strengths-list">
          <li v-for="str in strengths" :key="str" class="strength-item">
            <span class="chk-icon-box"><Check size="14" /></span>
            <span>{{ str }}</span>
          </li>
        </ul>
        
        <RouterLink to="/about" class="btn btn-primary about-btn">
          Read More About Us <ArrowRight size="16" />
        </RouterLink>
      </div>
      
      <!-- Col 2: Center culinary graphic (Cleaver slicing cutting board SVG) -->
      <div class="about-graphic">
        <div class="illustration-box">
          <svg viewBox="0 0 100 100" class="cutting-svg">
            <rect x="15" y="60" width="70" height="15" rx="3" fill="#8d5b4c" />
            <path d="M40,25 L65,15 L60,50 L40,55 Z" fill="#b0bec5" stroke="#37474f" stroke-width="2" />
            <line x1="60" y1="50" x2="72" y2="60" stroke="#8d5b4c" stroke-width="4" stroke-linecap="round" />
            <!-- Meat slices -->
            <rect x="25" y="52" width="12" height="8" rx="2" fill="#d32f2f" />
            <rect x="42" y="54" width="12" height="8" rx="2" fill="#d32f2f" />
          </svg>
        </div>
      </div>
      
      <!-- Col 3: Stat Badges -->
      <div class="about-badges">
        <div class="badge-card">
          <div class="badge-icon-box">
            <Award size="24" />
          </div>
          <div class="badge-info">
            <h3>10+ Years</h3>
            <p>Of Experience. Delivering Freshness Since 2014.</p>
          </div>
        </div>
        
        <div class="badge-card red-badge">
          <div class="badge-icon-box">
            <ShieldAlert size="24" />
          </div>
          <div class="badge-info">
            <h3>Safety First</h3>
            <p>We follow international ISO and Halal standards to ensure the best quality.</p>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>

<style scoped>
.about-section {
  background-color: var(--color-light);
  padding: 80px 0;
}

.about-grid {
  display: grid;
  grid-template-columns: 1.2fr 0.8fr 1fr;
  gap: 40px;
  align-items: center;
}

.text-left {
  text-align: left;
}

.text-left::after {
  margin: 12px 0 0;
}

.about-desc {
  font-size: 15px;
  line-height: 1.6;
  color: var(--color-text-muted);
  margin-top: 20px;
  margin-bottom: 12px;
}

.strengths-list {
  margin: 24px 0 32px;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.strength-item {
  display: flex;
  align-items: center;
  gap: 12px;
  font-weight: 700;
  font-size: 14px;
  color: var(--color-text-dark);
}

.chk-icon-box {
  background-color: rgba(0, 71, 27, 0.08);
  color: var(--color-primary);
  width: 24px;
  height: 24px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.about-btn {
  background-color: var(--color-primary);
}

.about-btn:hover {
  background-color: var(--color-primary-light);
  box-shadow: 0 4px 12px rgba(0, 71, 27, 0.2);
}

.about-graphic {
  display: flex;
  justify-content: center;
}

.illustration-box {
  width: 220px;
  height: 220px;
  background-color: var(--color-light-surface);
  border-radius: var(--border-radius-lg);
  border: 1px solid var(--color-border);
  padding: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.cutting-svg {
  width: 100%;
  height: 100%;
}

.about-badges {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.badge-card {
  background-color: var(--color-light-surface);
  border: 1px solid var(--color-border);
  padding: 24px;
  border-radius: var(--border-radius-md);
  display: flex;
  gap: 16px;
  transition: var(--transition-smooth);
}

.badge-card:hover {
  transform: translateY(-2px);
  border-color: var(--color-primary);
}

.badge-icon-box {
  background-color: rgba(0, 71, 27, 0.08);
  color: var(--color-primary);
  width: 48px;
  height: 48px;
  border-radius: var(--border-radius-sm);
  display: flex;
  justify-content: center;
  align-items: center;
  flex-shrink: 0;
}

.badge-info h3 {
  font-size: 18px;
  font-weight: 800;
  color: var(--color-text-dark);
  text-transform: uppercase;
  margin-bottom: 4px;
}

.badge-info p {
  font-size: 12px;
  color: var(--color-text-muted);
  line-height: 1.5;
}

.badge-card.red-badge {
  background-color: rgba(204, 41, 0, 0.02);
  border-color: rgba(204, 41, 0, 0.1);
}

.badge-card.red-badge:hover {
  border-color: var(--color-accent);
}

.badge-card.red-badge .badge-icon-box {
  background-color: rgba(204, 41, 0, 0.08);
  color: var(--color-accent);
}

@media (max-width: 992px) {
  .about-grid {
    grid-template-columns: 1.2fr 0.8fr;
  }
  .about-badges {
    grid-template-columns: 1fr 1fr;
    grid-column: span 2;
    flex-direction: row;
  }
}

@media (max-width: 768px) {
  .about-grid {
    grid-template-columns: 1fr;
  }
  .about-graphic {
    display: none;
  }
  .about-badges {
    grid-template-columns: 1fr;
    grid-column: span 1;
  }
}
</style>
