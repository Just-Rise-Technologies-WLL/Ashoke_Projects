<script setup>
import TopBar from '@/components/layout/TopBar.vue'
import Navbar from '@/components/layout/Navbar.vue'
import Footer from '@/components/layout/Footer.vue'
import { CheckCircle2 } from 'lucide-vue-next'
</script>

<template>
  <div class="page-view">
    <TopBar />
    <Navbar />
    
    <main>
      <!-- Page Header -->
      <div class="page-header">
        <div class="container">
          <span class="page-subtitle">Who We Are</span>
          <h1 class="page-title">About <span>MTN</span></h1>
        </div>
      </div>

      <!-- About Us Content Section -->
      <section class="about-section">
        <div class="container about-grid">
          
          <div class="about-content">
            <h2>Your Premier Auto Parts Partner in the Middle East</h2>
            <p>
              MTN Auto Spare Parts Trading L.L.C is a premier, Dubai-based distributor of high-quality automotive components. Established with a vision to deliver unmatched trust and quality, we supply a comprehensive range of passenger car, SUV, and commercial vehicle spare parts across the United Arab Emirates and the wider GCC region.
            </p>
            <p>
              Operating from our state-of-the-art warehouses located in Al Quoz Industrial Area 3, Dubai, we stock thousands of parts across multiple product lines. Whether you need critical engine components, braking systems, suspension parts, or premium lubricants, MTN is equipped to keep your wheels turning.
            </p>
            
            <div class="highlights-list">
              <div class="highlight-item">
                <CheckCircle2 size="20" class="chk-icon" />
                <span>100% Genuine and OEM Parts</span>
              </div>
              <div class="highlight-item">
                <CheckCircle2 size="20" class="chk-icon" />
                <span>Extensive Stock Availability</span>
              </div>
              <div class="highlight-item">
                <CheckCircle2 size="20" class="chk-icon" />
                <span>Fast & Reliable Logistics across UAE</span>
              </div>
              <div class="highlight-item">
                <CheckCircle2 size="20" class="chk-icon" />
                <span>Competitive Pricing Structures</span>
              </div>
            </div>
          </div>
          
          <!-- Visual Side Column (Sleek CSS/SVG box representing warehouse/quality) -->
          <div class="about-visual">
            <div class="visual-card">
              <div class="card-inner">
                <div class="brand-badge">MTN</div>
                <h3>Quality Guaranteed</h3>
                <p>All our parts undergo rigorous verification to ensure perfect fitment and longevity.</p>
                <div class="stamp-svg">
                  <svg viewBox="0 0 100 100" width="80" height="80">
                    <circle cx="50" cy="50" r="40" fill="none" stroke="rgba(220,38,38,0.2)" stroke-width="2" stroke-dasharray="3 3" />
                    <text x="50" y="55" font-size="12" font-weight="900" fill="rgba(220,38,38,0.4)" text-anchor="middle">GENUINE</text>
                  </svg>
                </div>
              </div>
            </div>
          </div>

        </div>
      </section>

      <!-- Mission & Vision Section -->
      <section class="mission-vision-section">
        <div class="container mv-grid">
          <div class="mv-card">
            <h3>Our Mission</h3>
            <p>
              To provide auto workshops, fleet owners, and retailers with an uninterrupted supply of top-tier spare parts, ensuring vehicle safety, performance, and reliability.
            </p>
          </div>
          <div class="mv-card">
            <h3>Our Vision</h3>
            <p>
              To become the most trusted and efficient automotive parts supply house in the GCC, recognized for our extensive product portfolio and client-first relationship approach.
            </p>
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
  color: var(--color-primary);
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
  color: var(--color-primary);
}

.about-section {
  padding: 80px 0;
}

.about-grid {
  display: grid;
  grid-template-columns: 1.2fr 0.8fr;
  gap: 50px;
  align-items: center;
}

.about-content h2 {
  font-size: 28px;
  font-weight: 900;
  color: var(--color-text-dark);
  margin-bottom: 20px;
  text-transform: uppercase;
}

.about-content p {
  color: var(--color-text-muted);
  line-height: 1.7;
  margin-bottom: 20px;
  font-size: 15px;
}

.highlights-list {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
  margin-top: 30px;
}

.highlight-item {
  display: flex;
  align-items: center;
  gap: 10px;
  font-weight: 700;
  color: var(--color-text-dark);
  font-size: 14px;
}

.chk-icon {
  color: var(--color-primary);
  flex-shrink: 0;
}

.about-visual {
  display: flex;
  justify-content: center;
}

.visual-card {
  background-color: var(--color-dark);
  color: white;
  padding: 40px;
  border-radius: var(--border-radius-lg);
  max-width: 340px;
  width: 100%;
  position: relative;
  overflow: hidden;
  border-left: 5px solid var(--color-primary);
  box-shadow: 0 15px 35px rgba(0,0,0,0.15);
}

.brand-badge {
  background-color: var(--color-primary);
  color: white;
  padding: 4px 10px;
  font-size: 11px;
  font-weight: 900;
  border-radius: 50px;
  display: inline-block;
  margin-bottom: 20px;
}

.visual-card h3 {
  font-size: 20px;
  font-weight: 900;
  margin-bottom: 12px;
  text-transform: uppercase;
}

.visual-card p {
  font-size: 14px;
  color: var(--color-text-light);
  line-height: 1.6;
}

.stamp-svg {
  margin-top: 20px;
  display: flex;
  justify-content: flex-end;
}

.mission-vision-section {
  background-color: var(--color-light-surface);
  padding: 80px 0;
}

.mv-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 30px;
}

.mv-card {
  background-color: var(--color-light);
  border: 1px solid var(--color-border);
  padding: 40px;
  border-radius: var(--border-radius-md);
  transition: var(--transition-smooth);
}

.mv-card:hover {
  transform: translateY(-4px);
  border-color: var(--color-primary);
  box-shadow: 0 8px 25px rgba(0,0,0,0.04);
}

.mv-card h3 {
  font-size: 20px;
  font-weight: 800;
  color: var(--color-primary);
  margin-bottom: 16px;
  text-transform: uppercase;
}

.mv-card p {
  color: var(--color-text-muted);
  line-height: 1.6;
  font-size: 14px;
}

@media (max-width: 992px) {
  .about-grid {
    grid-template-columns: 1fr;
    gap: 40px;
  }
  .about-visual {
    order: -1;
  }
}

@media (max-width: 768px) {
  .highlights-list {
    grid-template-columns: 1fr;
  }
  .mv-grid {
    grid-template-columns: 1fr;
  }
  .about-section {
    padding: 60px 0;
  }
  .mission-vision-section {
    padding: 60px 0;
  }
}
</style>
