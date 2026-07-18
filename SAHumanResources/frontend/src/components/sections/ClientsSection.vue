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
      
      <div class="clients-grid">
        <div v-for="(client, index) in clients" :key="index" class="client-logo-box">
          <img :src="client.img" :alt="client.name" class="client-img" />
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

.clients-grid {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 30px;
}

.client-logo-box {
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
  /* Optional: grayscale filter can create a professional uniform look */
  filter: grayscale(100%);
  opacity: 0.7;
  transition: all 0.3s ease;
}

.client-logo-box:hover .client-img {
  filter: grayscale(0%);
  opacity: 1;
}
</style>
