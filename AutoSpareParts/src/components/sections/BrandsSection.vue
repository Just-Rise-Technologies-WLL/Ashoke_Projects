<script setup>
const brands = [
  { name: 'Mercedes-Benz', style: 'font-family: serif; letter-spacing: 1px;' },
  { name: 'Volvo', style: 'font-family: sans-serif; font-weight: 800; text-transform: uppercase;' },
  { name: 'Kia', style: 'font-family: sans-serif; font-weight: 900; color: #c41230;' },
  { name: 'Hyundai', style: 'font-family: sans-serif; font-style: italic; font-weight: 800;' },
  { name: 'Nissan', style: 'font-family: sans-serif; font-weight: 700; letter-spacing: 2px;' },
  { name: 'Toyota', style: 'font-family: sans-serif; font-weight: 900; letter-spacing: 1px;' },
  { name: 'GMC', style: 'font-family: sans-serif; font-weight: 900; color: #dc2626; font-size: 24px;' },
  { name: 'Audi', style: 'font-family: sans-serif; font-weight: 500; letter-spacing: 2px;' },
  { name: 'Chrysler', style: 'font-family: serif; font-style: italic; font-weight: 700;' },
  { name: 'Jeep', style: 'font-family: sans-serif; font-weight: 900; letter-spacing: -0.5px;' },
  { name: 'Mitsubishi', style: 'font-family: sans-serif; font-weight: 800; color: #dc2626;' },
  { name: 'Ford', style: 'font-family: cursive; font-weight: 700; font-style: italic;' },
  { name: 'Honda', style: 'font-family: sans-serif; font-weight: 800; letter-spacing: 3px;' },
  { name: 'Jaguar', style: 'font-family: serif; font-style: italic; font-weight: 700;' },
  { name: 'Porsche', style: 'font-family: sans-serif; font-weight: 700; letter-spacing: 4px; font-size: 11px;' },
  { name: 'Isuzu', style: 'font-family: sans-serif; font-weight: 900; color: #dc2626;' },
  { name: 'Land Rover', style: 'font-family: sans-serif; font-weight: 700; color: #1e3a1e;' },
  { name: 'UD Trucks', style: 'font-family: sans-serif; font-weight: 800;' },
  { name: 'BMW', style: 'font-family: sans-serif; font-weight: 900; letter-spacing: 1px;' },
  { name: 'Daihatsu', style: 'font-family: sans-serif; font-weight: 700; font-style: italic;' },
  { name: 'Renault', style: 'font-family: sans-serif; font-weight: 300; letter-spacing: 3px;' },
  { name: 'Mopar', style: 'font-family: sans-serif; font-weight: 900; color: #0056b3;' },
  { name: 'Hino', style: 'font-family: sans-serif; font-weight: 900; font-style: italic; color: #dc2626;' },
  { name: 'Mazda', style: 'font-family: sans-serif; font-weight: 600; font-style: italic;' }
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
          <!-- Stylized logo placeholder representing high-end typography -->
          <div class="brand-logo-text" :style="brand.style">
            {{ brand.name }}
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
  padding: 10px;
  transition: var(--transition-smooth);
  user-select: none;
}

.brand-card:hover {
  border-color: var(--color-primary);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.05);
  transform: scale(1.02);
}

.brand-logo-text {
  font-size: 16px;
  font-weight: 700;
  color: var(--color-text-dark);
  text-align: center;
  opacity: 0.75;
  transition: var(--transition-smooth);
}

.brand-card:hover .brand-logo-text {
  opacity: 1;
  color: var(--color-primary);
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
  .brand-logo-text {
    font-size: 14px;
  }
}
</style>
