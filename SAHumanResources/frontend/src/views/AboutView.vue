<script setup>
import TopBar from '@/components/layout/TopBar.vue'
import Navbar from '@/components/layout/Navbar.vue'
import Footer from '@/components/layout/Footer.vue'
import WhyPartnerSection from '@/components/sections/WhyPartnerSection.vue'
import SectionHeader from '@/components/ui/SectionHeader.vue'
import { Target, Lightbulb, ShieldCheck } from 'lucide-vue-next'
</script>

<template>
  <div class="page-view">
    <TopBar />
    <Navbar />
    
    <main>
      <!-- Page Header -->
      <div class="page-header">
        <div class="container">
          <SectionHeader subtitle="Discover Our Journey" title="About Us" :centered="false" class="page-title-header" />
        </div>
      </div>

      <!-- About Content -->
      <section class="inner-about">
        <div class="container about-container">
          <div class="about-text-content">
            <h2>Building the Future with the Right Workforce</h2>
            <p>
              <b>SHAJAD AHMAD HR CONSULTANCIES L.L.C.</b> is a reputed Sharjah-based manpower supply and HR consultancy. We specialize in providing skilled and semi-skilled labor for the construction, fit-out, and building maintenance industries across the UAE.
            </p>
            <p>
              Over the years, we have built a profound understanding of the operational demands of large-scale projects. We bridge the gap between site-level operational demands and a vetted, ready-to-deploy workforce, offering scalable, fully compliant, and cost-effective staffing solutions.
            </p>
            <p>
              Our operations strictly comply with the Ministry of Human Resources and Emiratisation (MOHRE) regulations, ensuring a seamless, legal, and hassle-free experience for our clients.
            </p>
          </div>
          <div class="about-image-wrapper">
             <img src="https://images.unsplash.com/photo-1541888086425-d81bb19240f5?ixlib=rb-4.0.3&auto=format&fit=crop&w=1000&q=80" alt="Construction Work" class="inner-image" />
          </div>
        </div>
      </section>

      <!-- Vision & Mission -->
      <section class="vision-mission-section">
        <div class="container vm-container">
          <div class="vm-card">
            <Target size="48" class="vm-icon" />
            <h3>Our Mission</h3>
            <p>To provide high-quality, reliable, and compliant manpower solutions that empower businesses to scale operations efficiently while maintaining the highest worker welfare standards.</p>
          </div>
          <div class="vm-card">
            <Lightbulb size="48" class="vm-icon" />
            <h3>Our Vision</h3>
            <p>To be the most trusted and preferred manpower and HR consultancy partner in the UAE, driving growth in the construction and technical service sectors through dedicated human capital.</p>
          </div>
          <div class="vm-card">
            <ShieldCheck size="48" class="vm-icon" />
            <h3>Our Core Values</h3>
            <p>Integrity, Compliance, Excellence, Reliability. We believe in building lasting partnerships based on mutual trust and a shared commitment to project success.</p>
          </div>
        </div>
      </section>

      <WhyPartnerSection />
    </main>
    
    <Footer />
  </div>
</template>

<style scoped>
.page-view {
  background-color: var(--color-background);
}

.page-header {
  background-color: var(--color-surface);
  padding: 60px 0 40px;
  border-bottom: 1px solid var(--color-border);
}

:deep(.page-title-header .title) {
  font-size: 48px;
  color: var(--color-primary-dark);
}

.inner-about {
  padding: 80px 0;
}

.about-container {
  display: flex;
  gap: 50px;
  align-items: center;
}

.about-text-content {
  flex: 1;
}

.about-text-content h2 {
  font-size: 32px;
  font-weight: 800;
  color: var(--color-primary-dark);
  margin-bottom: 24px;
  line-height: 1.2;
}

.about-text-content p {
  font-size: 16px;
  color: var(--color-text-muted);
  line-height: 1.6;
  margin-bottom: 16px;
}

.about-image-wrapper {
  flex: 1;
  border-radius: var(--border-radius-lg);
  overflow: hidden;
  box-shadow: var(--shadow-lg);
}

.inner-image {
  width: 100%;
  height: auto;
  min-height: 400px;
  object-fit: cover;
}

/* Vision / Mission */
.vision-mission-section {
  padding: 80px 0;
  background-color: var(--color-primary-dark);
  color: white;
}

.vm-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 30px;
}

.vm-card {
  background-color: rgba(255, 255, 255, 0.05);
  padding: 40px;
  border-radius: var(--border-radius);
  border: 1px solid rgba(255, 255, 255, 0.1);
  transition: transform 0.3s ease;
}

.vm-card:hover {
  transform: translateY(-5px);
  background-color: rgba(255, 255, 255, 0.08);
}

.vm-icon {
  color: var(--color-accent);
  margin-bottom: 20px;
}

.vm-card h3 {
  color: white;
  margin-bottom: 15px;
  font-size: 20px;
  font-weight: 700;
}

.vm-card p {
  color: #eeeeee;
  font-size: 14px;
  line-height: 1.6;
}

@media (max-width: 992px) {
  .about-container {
    flex-direction: column;
  }
}
</style>
