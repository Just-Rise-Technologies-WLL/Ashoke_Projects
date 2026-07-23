<script setup>
import Navbar from '@/components/layout/Navbar.vue'
import Footer from '@/components/layout/Footer.vue'
import WholesaleSection from '@/components/sections/WholesaleSection.vue'
</script>

<template>
  <div class="page-view">
    <Navbar />
    
    <main>
      <!-- Page Header -->
      <div class="page-header">
        <div class="container">
          <span class="page-subtitle">B2B Sourcing Solutions</span>
          <h1 class="page-title">Wholesale <span>Supply</span></h1>
        </div>
      </div>

      <!-- Detail Info -->
      <section class="wholesale-detail-section">
        <div class="container detail-container">
          <h2>Bulk Halal Meat Sourcing for UAE Businesses</h2>
          <p>
            At Fresh Cuts Meat Trading FZCO, we are built to handle commercial-scale requirements. We supply supermarkets, hypermarkets, international hotel chains, fine-dining restaurants, and catering operations across all seven Emirates.
          </p>

          <div class="sectors-grid">
            <div class="sector-card">
              <h3>Supermarkets & Retail</h3>
              <p>Clean pre-packed retail trays, custom-labeled cuts, and consistent daily delivery slots to keep your display cabinets fresh.</p>
            </div>
            <div class="sector-card">
              <h3>Hotels & Restaurants</h3>
              <p>Strict portion-control cuts, premium marbled steaks, and select seafood trimmed exactly to your chef's specifications.</p>
            </div>
            <div class="sector-card">
              <h3>Catering & Institutions</h3>
              <p>High-volume primal cuts, bulk bone-in mutton, and chicken drumsticks designed for cost-efficient corporate menu planning.</p>
            </div>
          </div>
        </div>
      </section>

      <!-- Wholesale Form -->
      <WholesaleSection />
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

.wholesale-detail-section {
  padding: 80px 0 40px;
  background-color: #ffffff;
}

.detail-container h2 {
  font-size: 28px;
  font-weight: 900;
  color: var(--color-text-dark);
  margin-bottom: 16px;
  text-transform: uppercase;
  text-align: center;
}

.detail-container p {
  color: var(--color-text-muted);
  font-size: 15px;
  line-height: 1.7;
  max-width: 800px;
  margin: 0 auto 48px;
  text-align: center;
}

.sectors-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 30px;
}

.sector-card {
  background-color: var(--color-light-surface);
  border: 1px solid var(--color-border);
  padding: 30px;
  border-radius: var(--border-radius-md);
  transition: var(--transition-smooth);
}

.sector-card:hover {
  transform: translateY(-2px);
  border-color: var(--color-primary);
}

.sector-card h3 {
  font-size: 18px;
  font-weight: 800;
  color: var(--color-primary);
  margin-bottom: 12px;
  text-transform: uppercase;
}

.sector-card p {
  font-size: 13px;
  color: var(--color-text-muted);
  line-height: 1.6;
  text-align: left;
  margin-bottom: 0;
}

@media (max-width: 992px) {
  .sectors-grid {
    grid-template-columns: 1fr;
    gap: 20px;
  }
}
</style>
