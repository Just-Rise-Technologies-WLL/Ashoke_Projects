<script setup>
const brands = [
  { name: 'Mercedes-Benz', isSvg: true, svg: `<svg viewBox="0 0 100 100" class="brand-logo-svg"><circle cx="50" cy="50" r="38" fill="none" stroke="currentColor" stroke-width="3"/><path d="M50,12 L50,50 L17,69 M50,50 L83,69" stroke="currentColor" stroke-width="3" stroke-linejoin="round" stroke-linecap="round"/></svg>` },
  { name: 'Volvo', src: '/images/brands/volvo.svg' },
  { name: 'Kia', src: '/images/brands/kia.svg' },
  { name: 'Hyundai', src: '/images/brands/hyundai.svg' },
  { name: 'Nissan', src: '/images/brands/nissan.svg' },
  { name: 'Toyota', src: '/images/brands/toyota.svg' },
  { name: 'GMC', isSvg: true, svg: `<svg viewBox="0 0 100 100" class="brand-logo-svg"><text x="50" y="65" font-family="'Impact', sans-serif" font-weight="900" font-size="44" fill="#dc2626" text-anchor="middle" letter-spacing="1">GMC</text></svg>` },
  { name: 'Audi', src: '/images/brands/audi.svg' },
  { name: 'Chrysler', isSvg: true, svg: `<svg viewBox="0 0 100 100" class="brand-logo-svg"><path d="M10,50 Q30,30 50,50 Q70,30 90,50 Q70,70 50,50 Q30,70 10,50 Z" fill="none" stroke="currentColor" stroke-width="2"/><circle cx="50" cy="50" r="10" fill="currentColor"/><path d="M5,50 L95,50" stroke="currentColor" stroke-width="1"/></svg>` },
  { name: 'Jeep', src: '/images/brands/jeep.svg' },
  { name: 'Mitsubishi', src: '/images/brands/mitsubishi.svg' },
  { name: 'Ford', src: '/images/brands/ford.svg' },
  { name: 'Honda', src: '/images/brands/honda.svg' },
  { name: 'Jaguar', isSvg: true, svg: `<svg viewBox="0 0 100 100" class="brand-logo-svg"><path d="M10,55 Q20,35 38,42 Q50,47 62,40 Q75,32 90,50 Q75,60 55,54 Q35,48 10,55 Z" fill="currentColor"/></svg>` },
  { name: 'Porsche', src: '/images/brands/porsche.svg' },
  { name: 'Isuzu', isSvg: true, svg: `<svg viewBox="0 0 100 100" class="brand-logo-svg"><text x="50" y="65" font-family="'Outfit', sans-serif" font-weight="900" font-size="32" fill="#dc2626" text-anchor="middle" letter-spacing="2">ISUZU</text></svg>` },
  { name: 'Land Rover', isSvg: true, svg: `<svg viewBox="0 0 100 60" class="brand-logo-svg"><ellipse cx="50" cy="30" rx="45" ry="22" fill="#00471b" stroke="#ffffff" stroke-width="2"/><text x="50" y="35" font-family="'Impact', sans-serif" font-weight="900" font-size="11" fill="#ffffff" text-anchor="middle" letter-spacing="0.5">LAND ROVER</text></svg>` },
  { name: 'UD Trucks', isSvg: true, svg: `<svg viewBox="0 0 100 100" class="brand-logo-svg"><circle cx="50" cy="50" r="30" fill="#dc2626"/><text x="50" y="60" font-family="'Impact', sans-serif" font-weight="900" font-size="28" fill="#ffffff" text-anchor="middle">UD</text></svg>` },
  { name: 'BMW', src: '/images/brands/bmw.svg' },
  { name: 'Daihatsu', isSvg: true, svg: `<svg viewBox="0 0 100 100" class="brand-logo-svg"><path d="M25,20 L55,20 C70,20 80,32 80,50 C80,68 70,80 55,80 L25,80 Z M38,32 L38,68 L50,68 C60,68 66,60 66,50 C66,40 60,32 50,32 Z" fill="currentColor"/></svg>` },
  { name: 'Renault', src: '/images/brands/renault.svg' },
  { name: 'Mopar', isSvg: true, svg: `<svg viewBox="0 0 100 100" class="brand-logo-svg"><path d="M15,20 L40,65 L50,45 L60,65 L85,20 L70,20 L50,55 L30,20 Z" fill="#0056b3"/></svg>` },
  { name: 'Hino', isSvg: true, svg: `<svg viewBox="0 0 100 100" class="brand-logo-svg"><path d="M25,20 L38,20 L38,42 L62,42 L62,20 L75,20 L75,80 L62,80 L62,56 L38,56 L38,80 L25,80 Z" fill="#dc2626"/></svg>` },
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

      <div class="brands-grid">
        <div v-for="(brand, idx) in brands" :key="idx" class="brand-card">
          <div class="brand-wrapper">
            <!-- Logo container that fades out on hover -->
            <div class="brand-logo-content">
              <div v-if="brand.isSvg" class="brand-svg-container" v-html="brand.svg"></div>
              <img v-else :src="brand.src" :alt="brand.name" class="brand-logo-img" />
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
  transition: var(--transition-smooth);
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
