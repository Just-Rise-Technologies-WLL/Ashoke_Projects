<script setup>
import Navbar from '@/components/layout/Navbar.vue'
import Footer from '@/components/layout/Footer.vue'
import { ShieldCheck, Snowflake, Utensils, Heart } from 'lucide-vue-next'
</script>

<template>
  <div class="page-view">
    <Navbar />
    
    <main>
      <!-- Page Header -->
      <div class="page-header">
        <div class="container">
          <span class="page-subtitle">Safety & Hygiene</span>
          <h1 class="page-title">Quality <span>Standards</span></h1>
        </div>
      </div>

      <!-- Quality content -->
      <section class="quality-section">
        <div class="container quality-container">
          <h2>Uncompromising Commitment to Food Safety</h2>
          <p class="intro-text">
            Operating in the meat industry demands absolute vigilance. At Fresh Cuts, we implement a comprehensive quality control protocol at every step of the sourcing, storage, and transport phases.
          </p>

          <div class="pillars-grid">
            <div class="pillar-card">
              <Utensils class="pillar-icon" size="32" />
              <h3>100% Halal Compliance</h3>
              <p>We source exclusively from certified abattoirs that follow authentic Islamic slaughter procedures. All shipments come with verified Halal credentials.</p>
            </div>
            
            <div class="pillar-card">
              <Snowflake class="pillar-icon" size="32" />
              <h3>Unbroken Cold Chain</h3>
              <p>From custom storage lockers to refrigerated transport vans, we keep our meat under strictly monitored climates, preventing any thermal fluctuations.</p>
            </div>

            <div class="pillar-card">
              <ShieldCheck class="pillar-icon" size="32" />
              <h3>HACCP Guidelines</h3>
              <p>Our sorting and portioning units adhere strictly to Hazard Analysis Critical Control Point guidelines, minimizing biological risks.</p>
            </div>

            <div class="pillar-card">
              <Heart class="pillar-icon" size="32" />
              <h3>Worker Welfare & Hygiene</h3>
              <p>Our butchers and handlers undergo regular health screenings and sanitization training, utilizing clean sterile protective gear at all times.</p>
            </div>
          </div>
        </div>
      </section>
    </main>
    
    <Footer />
  </div>
</template>

<style scoped>
.page-view {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

main {
  flex-grow: 1;
}

.page-header {
  background-color: var(--color-light-surface);
  padding: 60px 0;
  border-bottom: 1px solid var(--color-border);
}

.page-subtitle {
  color: var(--color-accent);
  font-size: 13px;
  font-weight: 800;
  text-transform: uppercase;
  letter-spacing: 2px;
  margin-bottom: 8px;
  display: block;
}

.page-title {
  font-size: 42px;
  font-weight: 900;
  color: var(--color-text-dark);
  text-transform: uppercase;
}

.page-title span {
  color: var(--color-accent);
}

.quality-section {
  padding: 80px 0;
}

.quality-container h2 {
  font-size: 28px;
  font-weight: 900;
  color: var(--color-text-dark);
  margin-bottom: 16px;
  text-transform: uppercase;
  text-align: center;
}

.intro-text {
  color: var(--color-text-muted);
  font-size: 15px;
  line-height: 1.7;
  max-width: 800px;
  margin: 0 auto 50px;
  text-align: center;
}

.pillars-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 30px;
}

.pillar-card {
  background-color: var(--color-light-surface);
  border: 1px solid var(--color-border);
  padding: 40px;
  border-radius: var(--border-radius-md);
  transition: var(--transition-smooth);
}

.pillar-card:hover {
  border-color: var(--color-primary);
  transform: translateY(-2px);
}

.pillar-icon {
  color: var(--color-primary);
  margin-bottom: 20px;
}

.pillar-card h3 {
  font-size: 18px;
  font-weight: 800;
  color: var(--color-text-dark);
  margin-bottom: 12px;
  text-transform: uppercase;
}

.pillar-card p {
  font-size: 13px;
  color: var(--color-text-muted);
  line-height: 1.6;
}

@media (max-width: 768px) {
  .pillars-grid {
    grid-template-columns: 1fr;
  }
}
</style>
