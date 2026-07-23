<script setup>
import TopBar from '@/components/layout/TopBar.vue'
import Navbar from '@/components/layout/Navbar.vue'
import HeroSection from '@/components/sections/HeroSection.vue'
import FeaturesSection from '@/components/sections/FeaturesSection.vue'
import CategoriesSection from '@/components/sections/CategoriesSection.vue'
import BrandsSection from '@/components/sections/BrandsSection.vue'
import WhyChooseSection from '@/components/sections/WhyChooseSection.vue'
import Footer from '@/components/layout/Footer.vue'
</script>

<template>
  <div class="page-view">
    <TopBar />
    <Navbar />
    
    <main>
      <HeroSection />
      <FeaturesSection />
      <CategoriesSection />
      <BrandsSection />
      <WhyChooseSection />
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
</style>
