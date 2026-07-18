<script setup>
import TopBar from '@/components/layout/TopBar.vue'
import Navbar from '@/components/layout/Navbar.vue'
import HeroSection from '@/components/sections/HeroSection.vue'
import StatsSection from '@/components/sections/StatsSection.vue'
import AboutSection from '@/components/sections/AboutSection.vue'
import CoreServicesSection from '@/components/sections/CoreServicesSection.vue'
import ManpowerCategoriesSection from '@/components/sections/ManpowerCategoriesSection.vue'
import WhyPartnerSection from '@/components/sections/WhyPartnerSection.vue'
import ClientsSection from '@/components/sections/ClientsSection.vue'
import CtaBannerSection from '@/components/sections/CtaBannerSection.vue'
import Footer from '@/components/layout/Footer.vue'
</script>

<template>
  <div class="home-view">
    <TopBar />
    <Navbar />
    
    <main>
      <HeroSection />
      <StatsSection />
      <AboutSection />
      <CoreServicesSection />
      <ManpowerCategoriesSection />
      <WhyPartnerSection />
      <ClientsSection />
      <CtaBannerSection />
    </main>
    
    <Footer />
  </div>
</template>
