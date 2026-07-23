<script setup>
import TopBar from '@/components/layout/TopBar.vue'
import Navbar from '@/components/layout/Navbar.vue'
import Footer from '@/components/layout/Footer.vue'
</script>

<template>
  <div class="page-view">
    <TopBar />
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
            <h2>1. Supply Queries & Quotations</h2>
            <p>
              Submitting an inquiry through this website does not constitute a sales contract. Quotations sent by our sales office are valid for 7 business days from dispatch unless otherwise stated.
            </p>

            <h2>2. Fitment & Fit Verification</h2>
            <p>
              It is the buyer's responsibility to provide accurate VIN (Vehicle Identification Numbers) or part reference codes. MTN Auto Spare Parts Trading L.L.C is not liable for incorrect fitments resulting from faulty customer VIN specifications.
            </p>

            <h2>3. Intellectual Property</h2>
            <p>
              The MTN logo, site text, graphics, CSS, and interactive layout are the intellectual properties of MTN Auto Spare Parts Trading L.L.C and may not be copied or distributed without authorization.
            </p>

            <h2>4. Jurisdiction</h2>
            <p>
              These Terms & Conditions are governed by the corporate regulations and laws of the Emirate of Dubai and the federal laws of the United Arab Emirates.
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
