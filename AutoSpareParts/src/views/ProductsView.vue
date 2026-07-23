<script setup>
import { ref, computed } from 'vue'
import TopBar from '@/components/layout/TopBar.vue'
import Navbar from '@/components/layout/Navbar.vue'
import Footer from '@/components/layout/Footer.vue'
import { isRequestModalOpen } from '@/composables/useModal'
import { Search, Info, HelpCircle } from 'lucide-vue-next'

const searchQueryParams = ref('')
const selectedCategoryFilter = ref('All')

const categories = ['All', 'Engine Parts', 'Brake System', 'Suspension Parts', 'Filters', 'Electrical Parts', 'Body Parts', 'Oils & Fluids', 'Accessories']

const products = [
  // Engine Parts
  { name: 'Pistons & Rings Set', category: 'Engine Parts', code: 'EP-PST-08', desc: 'High-strength aluminum alloy pistons for optimal thermal transfer.' },
  { name: 'Engine Valves', category: 'Engine Parts', code: 'EP-VALV-12', desc: 'Precision hardened steel intake and exhaust valves.' },
  { name: 'Full Gasket Kit', category: 'Engine Parts', code: 'EP-GSK-99', desc: 'Complete engine sealing solution matching OEM specs.' },
  // Brakes
  { name: 'Ventilated Brake Discs', category: 'Brake System', code: 'BR-ROT-01', desc: 'High-carbon cast iron brake rotors with thermal ventilation.' },
  { name: 'Ceramic Brake Pads', category: 'Brake System', code: 'BR-PAD-02', desc: 'Low-dust, ultra-quiet ceramic friction formulation.' },
  { name: 'Brake Caliper Assembly', category: 'Brake System', code: 'BR-CAL-04', desc: 'Piston calipers with pre-lubricated guide pins.' },
  // Suspension
  { name: 'Shock Absorbers', category: 'Suspension Parts', code: 'SU-SHK-10', desc: 'Gas-charged twin-tube dampeners for ride stability.' },
  { name: 'Coil Springs', category: 'Suspension Parts', code: 'SU-SPR-15', desc: 'High-tensile cold-coiled steel load-bearing springs.' },
  { name: 'Control Arms', category: 'Suspension Parts', code: 'SU-ARM-22', desc: 'Steel arms with pre-pressed heavy-duty rubber bushings.' },
  // Filters
  { name: 'Spin-On Oil Filter', category: 'Filters', code: 'FL-OIL-33', desc: 'High-capacity synthetic blend filtration medium.' },
  { name: 'Engine Air Filter', category: 'Filters', code: 'FL-AIR-44', desc: 'Multi-layer pleated paper air intake filter element.' },
  { name: 'Cabin Pollen Filter', category: 'Filters', code: 'FL-CAB-55', desc: 'Activated carbon filter elements for fresh cabin air.' },
  // Electrical
  { name: 'Iridium Spark Plugs', category: 'Electrical Parts', code: 'EL-PLG-07', desc: 'Fine-wire iridium center electrode for stable ignition.' },
  { name: '12V Lead-Acid Battery', category: 'Electrical Parts', code: 'EL-BAT-88', desc: 'Maintenance-free starter battery with high cranking amps.' },
  { name: 'Alternator Assembly', category: 'Electrical Parts', code: 'EL-ALT-10', desc: 'Heavy-duty voltage-regulated charging generator.' },
  // Body Parts
  { name: 'Front Bumper Cover', category: 'Body Parts', code: 'BD-BMP-11', desc: 'Impact-resistant ABS plastic bumper fascia.' },
  { name: 'Side Wing Mirrors', category: 'Body Parts', code: 'BD-MIR-22', desc: 'Heated power-folding side mirrors with turn indicators.' },
  // Oils
  { name: 'Full Synthetic 5W-30 Motor Oil', category: 'Oils & Fluids', code: 'OL-SYN-05', desc: 'Advanced wear protection lubricant for modern engines.' },
  { name: 'DOT 4 Brake Fluid', category: 'Oils & Fluids', code: 'OL-DOT-04', desc: 'High boiling point hydraulic fluid for braking systems.' }
]

const filteredProducts = computed(() => {
  return products.filter(product => {
    const matchesCategory = selectedCategoryFilter.value === 'All' || product.category === selectedCategoryFilter.value
    const matchesSearch = product.name.toLowerCase().includes(searchQueryParams.value.toLowerCase()) || 
                          product.code.toLowerCase().includes(searchQueryParams.value.toLowerCase()) ||
                          product.category.toLowerCase().includes(searchQueryParams.value.toLowerCase())
    return matchesCategory && matchesSearch
  })
})

const selectCategory = (category) => {
  selectedCategoryFilter.value = category
}

const openQuotation = () => {
  isRequestModalOpen.value = true
}
</script>

<template>
  <div class="page-view">
    <TopBar />
    <Navbar />
    
    <main>
      <!-- Page Header -->
      <div class="page-header">
        <div class="container">
          <span class="page-subtitle">Product Catalog</span>
          <h1 class="page-title">Explore <span>Spare Parts</span></h1>
        </div>
      </div>

      <!-- Main Layout -->
      <section class="products-section">
        <div class="container products-grid-container">
          
          <!-- Left Sidebar filters -->
          <aside class="sidebar-filters">
            <h3 class="filter-title">Categories</h3>
            <ul class="filter-list">
              <li 
                v-for="cat in categories" 
                :key="cat"
                class="filter-item"
                :class="{ active: selectedCategoryFilter === cat }"
                @click="selectCategory(cat)"
              >
                {{ cat }}
              </li>
            </ul>
          </aside>

          <!-- Right Content Grid -->
          <div class="catalog-content">
            
            <!-- Search header -->
            <div class="search-box-wrapper">
              <Search size="20" class="search-icon" />
              <input 
                v-model="searchQueryParams" 
                type="text" 
                class="search-input" 
                placeholder="Search by part name, category or product code..."
              >
            </div>

            <!-- Products Listing -->
            <div v-if="filteredProducts.length > 0" class="products-list-grid">
              <div v-for="prod in filteredProducts" :key="prod.code" class="product-card">
                <div class="product-header">
                  <span class="product-category">{{ prod.category }}</span>
                  <span class="product-code">Code: {{ prod.code }}</span>
                </div>
                <h3 class="product-title">{{ prod.name }}</h3>
                <p class="product-desc">{{ prod.desc }}</p>
                <div class="product-footer">
                  <button @click="openQuotation" class="btn btn-primary quote-btn">
                    Request Quote
                  </button>
                </div>
              </div>
            </div>
            
            <!-- Empty state -->
            <div v-else class="empty-state">
              <HelpCircle size="48" class="empty-icon" />
              <h3>No Parts Found</h3>
              <p>We supply custom orders too. Click below to query our logistics experts directly.</p>
              <button @click="openQuotation" class="btn btn-primary">Request Custom Quotation</button>
            </div>

          </div>

        </div>
      </section>
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

.page-header {
  background-color: var(--color-light-surface);
  padding: 60px 0;
  border-bottom: 1px solid var(--color-border);
}

.page-subtitle {
  color: var(--color-primary);
  font-size: 13px;
  font-weight: 800;
  text-transform: uppercase;
  letter-spacing: 2px;
  margin-bottom: 8px;
  display: block;
}

.page-title {
  font-size: 42px;
  font-weight: 900;
  color: var(--color-text-dark);
  text-transform: uppercase;
}

.page-title span {
  color: var(--color-primary);
}

.products-section {
  padding: 60px 0;
  background-color: #ffffff;
}

.products-grid-container {
  display: grid;
  grid-template-columns: 260px 1fr;
  gap: 40px;
  align-items: start;
}

.sidebar-filters {
  background-color: var(--color-light-surface);
  border: 1px solid var(--color-border);
  border-radius: var(--border-radius-md);
  padding: 24px;
}

.filter-title {
  font-size: 16px;
  font-weight: 800;
  text-transform: uppercase;
  margin-bottom: 16px;
  color: var(--color-text-dark);
  border-bottom: 2px solid var(--color-primary);
  padding-bottom: 8px;
}

.filter-list {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.filter-item {
  padding: 10px 14px;
  font-size: 14px;
  font-weight: 700;
  border-radius: var(--border-radius-sm);
  color: var(--color-text-muted);
  cursor: pointer;
  transition: var(--transition-smooth);
}

.filter-item:hover {
  background-color: rgba(220, 38, 38, 0.05);
  color: var(--color-primary);
}

.filter-item.active {
  background-color: var(--color-primary);
  color: white;
}

.catalog-content {
  display: flex;
  flex-direction: column;
  gap: 30px;
}

.search-box-wrapper {
  display: flex;
  align-items: center;
  border: 1px solid var(--color-border);
  border-radius: var(--border-radius-sm);
  padding: 4px 16px;
  background-color: var(--color-light-surface);
  transition: var(--transition-smooth);
}

.search-box-wrapper:focus-within {
  border-color: var(--color-primary);
  box-shadow: 0 0 0 3px rgba(220, 38, 38, 0.1);
}

.search-icon {
  color: var(--color-text-muted);
  margin-right: 12px;
}

.search-input {
  width: 100%;
  padding: 12px 0;
  border: none;
  background: none;
  font-family: var(--font-sans);
  color: var(--color-text-dark);
}

.search-input:focus {
  outline: none;
}

.products-list-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

.product-card {
  background-color: white;
  border: 1px solid var(--color-border);
  border-radius: var(--border-radius-md);
  padding: 24px;
  display: flex;
  flex-direction: column;
  transition: var(--transition-smooth);
}

.product-card:hover {
  border-color: var(--color-primary);
  box-shadow: 0 10px 20px rgba(0,0,0,0.03);
  transform: translateY(-3px);
}

.product-header {
  display: flex;
  justify-content: space-between;
  margin-bottom: 12px;
  font-size: 11px;
  font-weight: 800;
  text-transform: uppercase;
}

.product-category {
  color: var(--color-primary);
}

.product-code {
  color: var(--color-text-muted);
}

.product-title {
  font-size: 17px;
  font-weight: 800;
  color: var(--color-text-dark);
  margin-bottom: 8px;
  line-height: 1.3;
}

.product-desc {
  font-size: 13px;
  color: var(--color-text-muted);
  line-height: 1.5;
  margin-bottom: 20px;
  flex-grow: 1;
}

.quote-btn {
  width: 100%;
  font-size: 12px;
  padding: 10px;
}

.empty-state {
  text-align: center;
  padding: 60px 20px;
  background-color: var(--color-light-surface);
  border-radius: var(--border-radius-md);
  border: 1px dashed var(--color-border);
}

.empty-icon {
  color: var(--color-text-light);
  margin-bottom: 16px;
}

.empty-state h3 {
  font-size: 20px;
  font-weight: 800;
  margin-bottom: 8px;
  text-transform: uppercase;
}

.empty-state p {
  color: var(--color-text-muted);
  font-size: 14px;
  margin-bottom: 24px;
  max-width: 400px;
  margin-left: auto;
  margin-right: auto;
}

@media (max-width: 1200px) {
  .products-list-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 992px) {
  .products-grid-container {
    grid-template-columns: 1fr;
    gap: 30px;
  }
  .sidebar-filters {
    display: none; /* In production mobile, this can turn into a dropdown filter */
  }
}

@media (max-width: 576px) {
  .products-list-grid {
    grid-template-columns: 1fr;
  }
}
</style>
