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
          <SectionHeader subtitle="Legal Information" title="Privacy Policy" :centered="false" class="page-title-header" />
        </div>
      </div>

      <!-- Content -->
      <section class="legal-content-section">
        <div class="container legal-container">
          <div class="legal-text">
            <h2>1. Information We Collect</h2>
            <p>
              We collect information that you voluntarily provide to us when you fill out forms on our website (such as the "Request Manpower" or "Contact Us" forms). This information may include your name, email address, phone number, company name, and details about your workforce requirements.
            </p>

            <h2>2. How We Use Your Information</h2>
            <p>
              We use the collected information to:
            </p>
            <ul>
              <li>Respond to your requests and inquiries.</li>
              <li>Provide, maintain, and improve our manpower supply and HR consultancy services.</li>
              <li>Comply with applicable local legal and regulatory requirements in the UAE.</li>
            </ul>

            <h2>3. Information Sharing and Disclosure</h2>
            <p>
              We do not sell, trade, or otherwise transfer your personal information to outside parties. This does not include trusted third parties who assist us in operating our website or conducting our business, so long as those parties agree to keep this information confidential. We may also release information when its release is appropriate to comply with the law.
            </p>

            <h2>4. Security of Your Information</h2>
            <p>
              We implement a variety of security measures to maintain the safety of your personal information. However, no method of transmission over the Internet is 100% secure, and we cannot guarantee absolute security.
            </p>

            <h2>5. Contact Us</h2>
            <p>
              If you have any questions regarding this Privacy Policy, you may contact us using the details below:
            </p>
            <p class="contact-details">
              <strong>Shajad Ahmad HR Consultancies L.L.C</strong><br>
              Sharjah, UAE<br>
              Email: <a href="mailto:info@shajadhrconsultancy.com">info@shajadhrconsultancy.com</a>
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

.legal-text ul {
  margin-bottom: 20px;
  padding-left: 20px;
}

.legal-text li {
  color: var(--color-text-main);
  margin-bottom: 8px;
  line-height: 1.6;
}

.contact-details {
  background-color: var(--color-surface);
  padding: 20px;
  border-left: 4px solid var(--color-primary);
  border-radius: 4px;
  margin-top: 20px;
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
  .legal-container {
    padding: 20px;
  }
}
</style>
