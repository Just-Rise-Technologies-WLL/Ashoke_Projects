<script setup>
import Navbar from '@/components/layout/Navbar.vue'
import Footer from '@/components/layout/Footer.vue'
</script>

<template>
  <div class="page-view">
    <Navbar />
    
    <main>
      <!-- Page Header -->
      <div class="page-header">
        <div class="container">
          <span class="page-subtitle">Legal Agreement</span>
          <h1 class="page-title">Terms & <span>Conditions</span></h1>
        </div>
      </div>

      <!-- Legal Content -->
      <section class="legal-content-section">
        <div class="container legal-container">
          <div class="legal-text">
            <h2>1. Sourcing & Delivery Queries</h2>
            <p>
              Submitting an inquiry through this website does not constitute a sales contract. Quotations sent by our sales office are subject to product availability and cold chain logistics scheduling.
            </p>

            <h2>2. Product Quality & Sourcing</h2>
            <p>
              Fresh Cuts Meat Trading FZCO guarantees all meat items are 100% Halal certified and kept in active temperature control throughout shipping. Buyers must inspect shipments at delivery to confirm quality.
            </p>

            <h2>3. Intellectual Property</h2>
            <p>
              The Fresh Cuts logo, text, graphics, CSS, and layout are the intellectual properties of Fresh Cuts Meat Trading FZCO and may not be copied or distributed without authorization.
            </p>

            <h2>4. Jurisdiction</h2>
            <p>
              These Terms & Conditions are governed by the corporate regulations and laws of the United Arab Emirates.
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

.legal-content-section {
  padding: 80px 0;
  background-color: #f6f7f6;
}

.legal-container {
  max-width: 800px;
  background: white;
  padding: 40px;
  border-radius: var(--border-radius-md, 8px);
  border: 1px solid var(--color-border);
  box-shadow: 0 4px 20px rgba(0,0,0,0.02);
}

.legal-text h2 {
  font-size: 20px;
  color: var(--color-text-dark);
  margin-top: 30px;
  margin-bottom: 12px;
  font-weight: 800;
  text-transform: uppercase;
}

.legal-text p {
  color: var(--color-text-muted);
  line-height: 1.7;
  margin-bottom: 20px;
}

@media (max-width: 768px) {
  .legal-content-section {
    padding: 40px 15px;
  }
}
</style>
