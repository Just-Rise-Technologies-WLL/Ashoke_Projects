<script setup>
import SectionHeader from '../ui/SectionHeader.vue'

// Array of uploaded client logos
const clients = [
  { name: 'ASGC', img: '/clients/asgc.jpeg' },
  { name: 'SNC/AL BAWANI', img: '/clients/snc.jpeg' },
  { name: 'MBM GULF', img: '/clients/mbmgulf.jpeg' },
  { name: 'ABC ARABIAN', img: '/clients/abc.jpeg' },
  { name: 'WORLD STAR', img: '/clients/worldstar.jpg' },
  { name: 'SEM SERVICES', img: '/clients/sem.jpeg' }
]
</script>

<template>
  <section class="clients-section">
    <div class="container">
      <SectionHeader subtitle="OUR CLIENTS" title="" :centered="true" />
      
      <div class="clients-marquee-container">
        <div class="clients-marquee-track">
          <!-- Duplicated clients array to ensure a seamless infinite scroll loop -->
          <div v-for="(client, index) in [...clients, ...clients, ...clients]" :key="index" class="client-logo-box">
            <img :src="client.img" :alt="client.name" class="client-img" />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.clients-section {
  padding: 60px 0 100px;
  background-color: white;
}

.clients-marquee-container {
  overflow: hidden;
  width: 100%;
  padding: 10px 0;
  position: relative;
}

/* Elegant fade out gradient on edges */
.clients-marquee-container::before,
.clients-marquee-container::after {
  content: "";
  height: 100%;
  width: 80px;
  position: absolute;
  top: 0;
  z-index: 2;
  pointer-events: none;
}
.clients-marquee-container::before {
  left: 0;
  background: linear-gradient(to right, rgba(255,255,255,1), rgba(255,255,255,0));
}
.clients-marquee-container::after {
  right: 0;
  background: linear-gradient(to left, rgba(255,255,255,1), rgba(255,255,255,0));
}

.clients-marquee-track {
  display: flex;
  gap: 30px;
  width: max-content;
  animation: scrollMarquee 25s linear infinite;
}

.clients-marquee-track:hover {
  animation-play-state: paused;
}

.client-logo-box {
  flex-shrink: 0;
  width: 160px;
  height: 80px;
  border: 1px solid #e2e8f0;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: var(--border-radius-sm);
  background-color: white;
  transition: all 0.3s ease;
  padding: 10px;
}

.client-logo-box:hover {
  border-color: var(--color-accent);
  box-shadow: var(--shadow-sm);
  transform: translateY(-2px);
}

.client-img {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
  filter: grayscale(100%);
  opacity: 0.7;
  transition: all 0.3s ease;
}

.client-logo-box:hover .client-img {
  filter: grayscale(0%);
  opacity: 1;
}

@keyframes scrollMarquee {
  0% {
    transform: translateX(0);
  }
  100% {
    /* 160px width + 30px gap = 190px. 6 unique elements */
    transform: translateX(calc(-190px * 6));
  }
}
</style>
