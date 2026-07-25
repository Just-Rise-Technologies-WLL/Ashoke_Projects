<script setup>
import { ref, onMounted } from 'vue'

const gridRef = ref(null)
const isVisible = ref(false)

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    if (entries[0].isIntersecting) {
      isVisible.value = true
      observer.disconnect()
    }
  }, {
    threshold: 0.1
  })
  
  if (gridRef.value) {
    observer.observe(gridRef.value)
  }
})

const brands = [
  { name: 'Mercedes-Benz', src: '/images/brands/mercedes.svg' },
  { name: 'Volvo', src: '/images/brands/volvo.svg' },
  { name: 'Kia', src: '/images/brands/kia.svg' },
  { name: 'Hyundai', src: '/images/brands/hyundai.svg' },
  { name: 'Nissan', src: '/images/brands/nissan.svg' },
  { name: 'Toyota', src: '/images/brands/toyota.svg' },
  { name: 'GMC', src: '/images/brands/gmc.svg' },
  { name: 'Audi', src: '/images/brands/audi.svg' },
  { name: 'Chrysler', src: '/images/brands/chrysler.svg' },
  { name: 'Jeep', src: '/images/brands/jeep.svg' },
  { name: 'Mitsubishi', src: '/images/brands/mitsubishi.svg' },
  { name: 'Ford', src: '/images/brands/ford.svg' },
  { name: 'Honda', src: '/images/brands/honda.svg' },
  { name: 'Jaguar', src: '/images/brands/jaguar.svg' },
  { name: 'Porsche', src: '/images/brands/porsche.svg' },
  { name: 'Isuzu', src: '/images/brands/isuzu.svg' },
  { name: 'Land Rover', src: '/images/brands/landrover.svg' },
  { name: 'UD Trucks', src: '/images/brands/udtrucks.svg' },
  { name: 'BMW', src: '/images/brands/bmw.svg' },
  { name: 'Daihatsu', src: '/images/brands/daihatsu.svg' },
  { name: 'Renault', src: '/images/brands/renault.svg' },
  { name: 'Mopar', src: '/images/brands/mopar.svg' },
  { name: 'Hino', src: '/images/brands/hino.svg' },
  { name: 'Mazda', src: '/images/brands/mazda.svg' }
]
</script>

<template>
  <section class="brands-section">
    <div class="container">
      
      <div class="section-header">
        <span class="section-subtitle">Supported Fleets</span>
        <h2 class="section-title">Top Brands <span>We Supply</span></h2>
      </div>

      <div ref="gridRef" class="brands-grid">
        <div 
          v-for="(brand, idx) in brands" 
          :key="idx" 
          class="brand-card"
          :class="{ 'animate-in': isVisible }"
          :style="{ '--delay': isVisible ? (idx * 40) + 'ms' : '0ms' }"
        >
          <div class="brand-wrapper">
            <!-- Logo container that fades out on hover -->
            <div class="brand-logo-content">
              <img :src="brand.src" :alt="brand.name" class="brand-logo-img" />
            </div>
            <!-- Name that fades in on hover -->
            <div class="brand-name-hover">
              {{ brand.name }}
            </div>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>

<style scoped>
.brands-section {
  background-color: var(--color-light);
  padding: 80px 0;
  border-bottom: 1px solid var(--color-border);
}

.brands-grid {
  display: grid;
  grid-template-columns: repeat(6, 1fr);
  gap: 20px;
}

.brand-card {
  height: 90px;
  background-color: var(--color-light);
  border: 1px solid var(--color-border);
  border-radius: var(--border-radius-sm);
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 15px;
  position: relative;
  overflow: hidden;
  opacity: 0;
  transform: translateY(20px);
  /* Use specific transition timings; only opacity and transform use the staggered --delay */
  transition: opacity 0.6s cubic-bezier(0.16, 1, 0.3, 1) var(--delay, 0ms), 
              transform 0.6s cubic-bezier(0.16, 1, 0.3, 1) var(--delay, 0ms),
              border-color 0.3s ease 0ms,
              box-shadow 0.3s ease 0ms;
}

.brand-card.animate-in {
  opacity: 1;
  transform: translateY(0);
}

.brand-card:hover {
  border-color: var(--color-primary);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.05);
}

.brand-wrapper {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
}

.brand-logo-content {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  opacity: 1;
  transform: scale(1);
  transition: var(--transition-smooth);
}

.brand-card:hover .brand-logo-content {
  opacity: 0;
  transform: scale(0.9);
}

.brand-logo-img {
  max-width: 95%;
  max-height: 95%;
  object-fit: contain;
  filter: grayscale(1) opacity(0.6);
  transition: var(--transition-smooth);
}

.brand-card:hover .brand-logo-img {
  filter: grayscale(0) opacity(1);
}

.brand-svg-container {
  width: 80px;
  height: 80px;
  display: flex;
  justify-content: center;
  align-items: center;
  color: var(--color-text-muted);
  opacity: 0.6;
  transition: var(--transition-smooth);
}

.brand-card:hover .brand-svg-container {
  color: var(--color-primary);
  opacity: 1;
}

.brand-name-hover {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%) scale(0.9);
  font-size: 13px;
  font-weight: 900;
  text-transform: uppercase;
  color: var(--color-primary);
  text-align: center;
  opacity: 0;
  letter-spacing: 0.5px;
  line-height: 1.2;
  width: 90%;
  pointer-events: none;
  transition: var(--transition-smooth);
}

.brand-card:hover .brand-name-hover {
  opacity: 1;
  transform: translate(-50%, -50%) scale(1);
}

:deep(.brand-logo-svg) {
  width: 100%;
  height: 100%;
  max-width: 75px;
  max-height: 75px;
}

@media (max-width: 1200px) {
  .brands-grid {
    grid-template-columns: repeat(4, 1fr);
  }
}

@media (max-width: 768px) {
  .brands-grid {
    grid-template-columns: repeat(3, 1fr);
    gap: 12px;
  }
  .brands-section {
    padding: 60px 0;
  }
}

@media (max-width: 480px) {
  .brands-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}
</style>
