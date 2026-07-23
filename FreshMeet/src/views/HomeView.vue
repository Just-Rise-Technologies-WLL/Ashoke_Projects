<script setup>
import TopBar from '@/components/layout/Navbar.vue' // FreshMeet navbar acts as top headers
import HeroSection from '@/components/sections/HeroSection.vue'
import FeaturesSection from '@/components/sections/FeaturesSection.vue'
import CategoriesSection from '@/components/sections/CategoriesSection.vue'
import AboutSection from '@/components/sections/AboutSection.vue'
import StatsSection from '@/components/sections/StatsSection.vue'
import WholesaleSection from '@/components/sections/WholesaleSection.vue'
import Footer from '@/components/layout/Footer.vue'
</script>

<template>
  <div class="page-view">
    <TopBar />
    
    <main>
      <HeroSection />
      <FeaturesSection />
      <CategoriesSection />
      <AboutSection />
      <StatsSection />
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
</style>
