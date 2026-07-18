<script setup>
import TopBar from '@/components/layout/TopBar.vue'
import Navbar from '@/components/layout/Navbar.vue'
import Footer from '@/components/layout/Footer.vue'
import SectionHeader from '@/components/ui/SectionHeader.vue'
import CtaBannerSection from '@/components/sections/CtaBannerSection.vue'

// 13 Categories based on the user's design request
const categories = [
  { title: 'Aluminium Fitter', img: 'https://images.unsplash.com/photo-1502014822147-1aedfb0676e0?auto=format&fit=crop&w=600&q=80' },
  { title: 'Setting Carpenter', img: 'https://images.unsplash.com/photo-1622345097495-236b32add1e4?auto=format&fit=crop&w=600&q=80' },
  { title: 'Furniture Carpenter', img: 'https://images.unsplash.com/photo-1540569014015-19a7be504e3a?auto=format&fit=crop&w=600&q=80' },
  { title: 'Wall Painting', img: 'https://images.unsplash.com/photo-1562259949-e8e7689d7828?auto=format&fit=crop&w=600&q=80' },
  { title: 'Mason', img: 'https://images.unsplash.com/photo-1605810230434-7631ac76ec81?auto=format&fit=crop&w=600&q=80' },
  { title: 'Rigger', img: 'https://images.unsplash.com/photo-1504307651254-35680f356f12?auto=format&fit=crop&w=600&q=80' },
  { title: 'Helper', img: 'https://images.unsplash.com/photo-1589939705384-5185137a7f05?auto=format&fit=crop&w=600&q=80' },
  { title: 'Plumber', img: 'https://images.unsplash.com/photo-1585704160432-721245fa8108?auto=format&fit=crop&w=600&q=80' },
  { title: 'Steel Fixer', img: 'https://images.unsplash.com/photo-1503387837-b154d5074bd2?auto=format&fit=crop&w=600&q=80' },
  { title: 'Pipe Fitter', img: 'https://images.unsplash.com/photo-1607567746777-6f81e6e06b38?auto=format&fit=crop&w=600&q=80' },
  { title: 'Welder', img: 'https://images.unsplash.com/photo-1506466010722-395aa28fc8ce?auto=format&fit=crop&w=600&q=80' },
  { title: 'Electrician', img: 'https://images.unsplash.com/photo-1621905251189-08b45d6a269e?auto=format&fit=crop&w=600&q=80' },
  { title: 'Duct Man', img: 'https://images.unsplash.com/photo-1625471138244-640a3dd9aaef?auto=format&fit=crop&w=600&q=80' }
]
</script>

<template>
  <div class="page-view">
    <TopBar />
    <Navbar />
    
    <main>
      <!-- Page Header -->
      <div class="page-header">
        <div class="container">
          <SectionHeader subtitle="SECTORS WE SUPPORT" title="Industries We Serve" :centered="false" class="page-title-header" />
        </div>
      </div>

      <section class="industries-section">
        <!-- SVG background pattern resembling the topo lines in the requested design -->
        <div class="bg-pattern"></div>
        
        <div class="container">
          <p class="intro-text">
            SHAJAD AHMAD HR CONSULTANCIES supports a wide spectrum of technical and heavy industries across the UAE. Below are the specialized manpower categories we proudly supply:
          </p>

          <div class="visual-grid">
            <div v-for="(cat, idx) in categories" :key="idx" class="visual-item" :class="'item-' + (idx % 2)">
              <div class="img-wrapper">
                <img :src="cat.img" :alt="cat.title" class="vis-img" />
                <div class="vis-label">{{ cat.title }}</div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <CtaBannerSection />
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

.industries-section {
  padding: 80px 0;
  background-color: #f6f7f6; /* Very light cream/gray like the screenshot */
  position: relative;
  overflow: hidden;
}

/* Recreating the organic wavy background pattern */
.bg-pattern {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  opacity: 0.2;
  background-image: 
    radial-gradient(ellipse at center, transparent 0%, transparent 60%, rgba(0, 71, 27, 0.05) 60%),
    repeating-radial-gradient(ellipse at 0% 0%, transparent 0%, transparent 100px, rgba(0, 71, 27, 0.05) 100px, rgba(0, 71, 27, 0.05) 102px);
}

.intro-text {
  max-width: 800px;
  font-size: 16px;
  color: var(--color-text-muted);
  line-height: 1.6;
  margin-bottom: 60px;
  position: relative;
  z-index: 2;
}

/* Standard Grid View */
.visual-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 40px;
  padding-bottom: 80px;
  position: relative;
  z-index: 2;
}

.visual-item {
  width: 100%;
}

.img-wrapper {
  position: relative;
  width: 100%;
  border-radius: var(--border-radius-lg);
  overflow: hidden;
  box-shadow: var(--shadow-sm);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.img-wrapper:hover {
  transform: translateY(-8px);
  box-shadow: var(--shadow-lg);
}

.vis-img {
  width: 100%;
  height: 280px;
  object-fit: cover;
  display: block;
  transition: transform 0.5s ease;
}

.img-wrapper:hover .vis-img {
  transform: scale(1.05);
}

.vis-label {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  background-color: rgba(35, 84, 34, 0.95); /* Specific green from screenshot with slight transparency */
  color: white;
  padding: 18px;
  font-size: 18px;
  font-family: var(--font-family);
  font-weight: 700;
  letter-spacing: 0.5px;
  text-align: center;
  backdrop-filter: blur(4px);
}

/* Responsive constraints */
@media (max-width: 900px) {
  .visual-grid {
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 30px;
  }
}
</style>
