<script setup>
import Navbar from '@/components/layout/Navbar.vue'
import Footer from '@/components/layout/Footer.vue'
import WholesaleSection from '@/components/sections/WholesaleSection.vue' // Contact form is reused from WholesaleSection
</script>

<template>
  <div class="page-view">
    <Navbar />
    
    <main>
      <!-- Page Header -->
      <div class="page-header">
        <div class="container">
          <span class="page-subtitle">Get In Touch</span>
          <h1 class="page-title">Contact <span>Fresh Cuts</span></h1>
        </div>
      </div>

      <!-- Wholesale section contains the full contact grid and form -->
      <WholesaleSection />
    </main>
    
    <Footer />
  </div>
</template>

<style>
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
</style>
