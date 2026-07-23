<script setup>
import Navbar from '@/components/layout/Navbar.vue'
import Footer from '@/components/layout/Footer.vue'
import { CheckCircle2 } from 'lucide-vue-next'
</script>

<template>
  <div class="page-view">
    <Navbar />
    
    <main>
      <!-- Page Header -->
      <div class="page-header">
        <div class="container">
          <span class="page-subtitle">Discover Our Roots</span>
          <h1 class="page-title">About <span>Fresh Cuts</span></h1>
        </div>
      </div>

      <!-- About Us Content Section -->
      <section class="about-details-section">
        <div class="container about-grid">
          
          <div class="about-text">
            <h2>Pioneers in Cold Chain Halal Meat Supply</h2>
            <p>
              Fresh Cuts Meat Trading FZCO is a reputed, Sharjah-based distributor specializing in fresh meat, chicken, beef, and seafood products. Serving clients across the UAE, we are committed to providing premium products that adhere to global health, safety, and halal processing guidelines.
            </p>
            <p>
              Operating from our dedicated cold storage facilities, we supply to supermarkets, catering establishments, restaurants, and wholesale traders. Our seamless temperature-controlled cold chain logistics ensure all meats are delivered at optimal temperatures, preserving peak freshness.
            </p>
            
            <div class="strengths-checklist">
              <div class="chk-item">
                <CheckCircle2 size="18" class="chk-icon" />
                <span>100% Halal certified sourcing channels</span>
              </div>
              <div class="chk-item">
                <CheckCircle2 size="18" class="chk-icon" />
                <span>Temperature-monitored refrigerated transport</span>
              </div>
              <div class="chk-item">
                <CheckCircle2 size="18" class="chk-icon" />
                <span>ISO & HACCP compliant handling procedures</span>
              </div>
              <div class="chk-item">
                <CheckCircle2 size="18" class="chk-icon" />
                <span>Flexible wholesale volume contracts</span>
              </div>
            </div>
          </div>
          
          <div class="about-infographics">
            <div class="info-box dark-box">
              <h3>Our Quality Oath</h3>
              <p>We do not compromise. All meat batches are verified for cut accuracy, fat content, and microbiological safety before shipping.</p>
            </div>
          </div>

        </div>
      </section>

      <!-- Mission / Vision -->
      <section class="mission-vision-section">
        <div class="container mv-grid">
          <div class="mv-card">
            <h3>Our Mission</h3>
            <p>To supply premium, safe, and ethically processed halal meat and seafood solutions that elevate the culinary standards of homes, hospitality, and businesses across the UAE.</p>
          </div>
          <div class="mv-card">
            <h3>Our Vision</h3>
            <p>To become the leading name in cold chain meat logistics and distribution in the region, recognized for hygiene excellence, reliable supply networks, and customer trust.</p>
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

.about-details-section {
  padding: 80px 0;
}

.about-grid {
  display: grid;
  grid-template-columns: 1.2fr 0.8fr;
  gap: 50px;
  align-items: center;
}

.about-text h2 {
  font-size: 28px;
  font-weight: 900;
  color: var(--color-text-dark);
  margin-bottom: 20px;
  text-transform: uppercase;
}

.about-text p {
  color: var(--color-text-muted);
  line-height: 1.7;
  margin-bottom: 20px;
  font-size: 15px;
}

.strengths-checklist {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
  margin-top: 30px;
}

.chk-item {
  display: flex;
  align-items: center;
  gap: 10px;
  font-weight: 700;
  color: var(--color-text-dark);
  font-size: 14px;
}

.chk-icon {
  color: var(--color-accent);
  flex-shrink: 0;
}

.about-infographics {
  display: flex;
  justify-content: center;
}

.info-box {
  background-color: var(--color-primary);
  color: white;
  padding: 40px;
  border-radius: var(--border-radius-lg);
  max-width: 340px;
  width: 100%;
  border-left: 5px solid var(--color-accent);
  box-shadow: 0 15px 35px rgba(0, 71, 27, 0.15);
}

.info-box h3 {
  font-size: 20px;
  font-weight: 900;
  margin-bottom: 12px;
  text-transform: uppercase;
}

.info-box p {
  font-size: 14px;
  color: var(--color-text-light);
  line-height: 1.6;
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
  border-color: var(--color-accent);
  box-shadow: 0 8px 25px rgba(0,0,0,0.04);
}

.mv-card h3 {
  font-size: 20px;
  font-weight: 800;
  color: var(--color-accent);
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
  .about-infographics {
    order: -1;
  }
}

@media (max-width: 768px) {
  .strengths-checklist {
    grid-template-columns: 1fr;
  }
  .mv-grid {
    grid-template-columns: 1fr;
  }
  .about-details-section {
    padding: 60px 0;
  }
  .mission-vision-section {
    padding: 60px 0;
  }
}
</style>
