<script setup>
import TopBar from '@/components/layout/TopBar.vue'
import Navbar from '@/components/layout/Navbar.vue'
import Footer from '@/components/layout/Footer.vue'
import SectionHeader from '@/components/ui/SectionHeader.vue'
</script>

<template>
  <div class="page-view">
    <TopBar />
    <Navbar />
    
    <main>
      <!-- Page Header -->
      <div class="page-header">
        <div class="container">
          <SectionHeader subtitle="Agreement" title="Terms & Conditions" :centered="false" class="page-title-header" />
        </div>
      </div>

      <!-- Content -->
      <section class="legal-content-section">
        <div class="container legal-container">
          <div class="legal-text">
            <h2>1. Acceptance of Terms</h2>
            <p>
              By accessing and using this website, you accept and agree to be bound by the terms and provision of this agreement. If you do not agree to abide by these terms, please do not use this site.
            </p>

            <h2>2. Provision of Services</h2>
            <p>
              This website provides information about our manpower supply, skilled/semi-skilled workforce recruitment, and HR consultancy services across the UAE. The submission of forms on this site constitutes a request for contact and does not guarantee the formal engagement of manpower services. A formal commercial contract is required to initiate any manpower deployment.
            </p>

            <h2>3. Intellectual Property</h2>
            <p>
              All content, logo design, text, graphics, and layouts on this website are the property of Shajad Ahmad HR Consultancies L.L.C and are protected by applicable intellectual property laws.
            </p>

            <h2>4. Limitation of Liability</h2>
            <p>
              In no event shall Shajad Ahmad HR Consultancies L.L.C be liable for any direct, indirect, incidental, or consequential damages arising out of the use or inability to use the information and services provided on this website.
            </p>

            <h2>5. Governing Law</h2>
            <p>
              These Terms & Conditions are governed by and construed in accordance with the laws of the United Arab Emirates. Any dispute arising out of your use of this website shall be subject to the exclusive jurisdiction of the UAE courts.
            </p>
          </div>
        </div>
      </section>
    </main>
    
    <Footer />
  </div>
</template>

<style scoped>
.page-header {
  background-color: var(--color-surface);
  padding: 60px 0 40px;
  border-bottom: 1px solid var(--color-border);
}

:deep(.page-title-header .title) {
  font-size: 48px;
  color: var(--color-primary-dark);
}

.legal-content-section {
  padding: 80px 0;
  background-color: #f6f7f6;
}

.legal-container {
  max-width: 800px;
  background: white;
  padding: 40px;
  border-radius: var(--border-radius-lg, 12px);
  box-shadow: 0 4px 20px rgba(0,0,0,0.05);
}

.legal-text h2 {
  font-size: 22px;
  color: var(--color-primary-dark);
  margin-top: 30px;
  margin-bottom: 15px;
  font-weight: 800;
}

.legal-text p {
  color: var(--color-text-main);
  line-height: 1.7;
  margin-bottom: 20px;
}

@media (max-width: 768px) {
  .legal-content-section {
    padding: 40px 15px;
  }
  .legal-container {
    padding: 20px;
  }
}
</style>
