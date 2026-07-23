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
          <span class="page-subtitle">Legal Information</span>
          <h1 class="page-title">Privacy <span>Policy</span></h1>
        </div>
      </div>

      <!-- Legal Content -->
      <section class="legal-content-section">
        <div class="container legal-container">
          <div class="legal-text">
            <h2>1. Information Collection</h2>
            <p>
              We collect information that you voluntarily provide when you submit a "Request Quotation" or "Contact Us" inquiry. This may include your company name, contact details, email address, phone number, and parts lists.
            </p>

            <h2>2. Purpose of Use</h2>
            <p>
              Your information is exclusively used to fulfill your quotation inquiries, confirm fitment compatibility, organize shipping logisitics, and handle client inquiries.
            </p>

            <h2>3. Secure Processing</h2>
            <p>
              We implement industry-standard secure socket layers and data controls to safeguard all inquiry sheets. We do not sell or lease client contact databases to third parties.
            </p>

            <h2>4. Corporate Contacts</h2>
            <p>
              For inquiries regarding data records, please reach out to:
            </p>
            <p class="contact-details">
              <strong>MTN Auto Spare Parts Trading L.L.C</strong><br>
              Al Quoz Industrial Area 3, Dubai, UAE<br>
              Email: <a href="mailto:info@mtnautospareparts.com">info@mtnautospareparts.com</a>
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

.contact-details {
  background-color: var(--color-light-surface);
  padding: 20px;
  border-left: 4px solid var(--color-primary);
  border-radius: 4px;
  margin-top: 20px;
  font-size: 14px;
}

.contact-details a {
  color: var(--color-primary);
  text-decoration: none;
  font-weight: 700;
}
.contact-details a:hover {
  text-decoration: underline;
}

@media (max-width: 768px) {
  .legal-content-section {
    padding: 40px 15px;
  }
}
</style>
