<script setup>
import { ref, computed } from 'vue'
import Navbar from '@/components/layout/Navbar.vue'
import Footer from '@/components/layout/Footer.vue'
import { isQuoteModalOpen } from '@/composables/useModal'
import { Search, HelpCircle } from 'lucide-vue-next'

const searchQueryParams = ref('')
const selectedCategory = ref('All')

const categories = ['All', 'Fresh Seafood', 'Fresh Chicken', 'Premium Beef', 'Lamb & Mutton']

const products = [
  // Seafood
  { name: 'Fresh Atlantic Salmon Fillet', category: 'Fresh Seafood', code: 'SF-SLM-01', desc: 'Premium grade, skin-on boneless salmon fillets rich in Omega-3.' },
  { name: 'White Tiger Prawns', category: 'Fresh Seafood', code: 'SF-PRW-02', desc: 'Jumbo prawns, cleaned and deveined, perfect for grills.' },
  { name: 'Local Sea Bream (Cipura)', category: 'Fresh Seafood', code: 'SF-SBR-03', desc: 'Whole cleaned sea bream, freshly caught and scaled.' },
  // Chicken
  { name: 'Fresh Whole Chicken', category: 'Fresh Chicken', code: 'CH-WHL-10', desc: 'Halal whole chicken, cleaned and ready for roasting.' },
  { name: 'Tender Chicken Breast Fillet', category: 'Fresh Chicken', code: 'CH-BST-12', desc: 'Skinless, boneless chicken breast portions, lean and tender.' },
  { name: 'Fresh Chicken Drumsticks', category: 'Fresh Chicken', code: 'CH-DRM-14', desc: 'Meaty chicken drumsticks, perfect for curries and baking.' },
  // Beef
  { name: 'Premium Angus Ribeye Steak', category: 'Premium Beef', code: 'BF-RBY-20', desc: 'Highly marbled, grain-fed Angus ribeye cuts.' },
  { name: 'Beef Tenderloin (Fillet Mignon)', category: 'Premium Beef', code: 'BF-TND-22', desc: 'Ultra-tender center-cut beef tenderloin steaks.' },
  { name: 'Premium Ground Beef (Minced)', category: 'Premium Beef', code: 'BF-MNC-25', desc: 'Lean minced beef, prepared daily from fresh chuck cuts.' },
  // Mutton
  { name: 'Fresh Lamb Chops', category: 'Lamb & Mutton', code: 'MT-CHP-30', desc: 'Tender Australian lamb loin chops, ready for grilling.' },
  { name: 'Mutton Curry Cuts (Bone-In)', category: 'Lamb & Mutton', code: 'MT-CUT-32', desc: 'Juicy shoulder and leg chunks, perfect for slow cooking.' }
]

const filteredProducts = computed(() => {
  return products.filter(product => {
    const matchesCategory = selectedCategory.value === 'All' || product.category === selectedCategory.value
    const matchesSearch = product.name.toLowerCase().includes(searchQueryParams.value.toLowerCase()) || 
                          product.code.toLowerCase().includes(searchQueryParams.value.toLowerCase()) ||
                          product.category.toLowerCase().includes(searchQueryParams.value.toLowerCase())
    return matchesCategory && matchesSearch
  })
})

const selectCategory = (category) => {
  selectedCategory.value = category
}

const openQuote = () => {
  isQuoteModalOpen.value = true
}
</script>

<template>
  <div class="page-view">
    <Navbar />
    
    <main>
      <!-- Page Header -->
      <div class="page-header">
        <div class="container">
          <span class="page-subtitle">Premium Cuts</span>
          <h1 class="page-title">Explore <span>Our Products</span></h1>
        </div>
      </div>

      <!-- Main Layout -->
      <section class="products-section">
        <div class="container products-grid-container">
          
          <!-- Left Sidebar filters -->
          <aside class="sidebar-filters">
            <h3 class="filter-title">Meat Categories</h3>
            <ul class="filter-list">
              <li 
                v-for="cat in categories" 
                :key="cat"
                class="filter-item"
                :class="{ active: selectedCategory === cat }"
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
                placeholder="Search by product name, cut, or item code..."
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
                  <button @click="openQuote" class="btn btn-primary quote-btn">
                    Request Quote
                  </button>
                </div>
              </div>
            </div>
            
            <!-- Empty state -->
            <div v-else class="empty-state">
              <HelpCircle size="48" class="empty-icon" />
              <h3>No Cuts Found</h3>
              <p>We source custom wholesale weights and specialty cuts. Contact our cold chain logistics desk.</p>
              <button @click="openQuote" class="btn btn-primary">Request Custom Sourcing</button>
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
  color: var(--color-accent);
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
  color: var(--color-accent);
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
  border-bottom: 2px solid var(--color-accent);
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
  background-color: rgba(204, 41, 0, 0.05);
  color: var(--color-accent);
}

.filter-item.active {
  background-color: var(--color-accent);
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
  border-color: var(--color-accent);
  box-shadow: 0 0 0 3px rgba(204, 41, 0, 0.1);
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
  box-shadow: 0 10px 20px rgba(0,71,27,0.03);
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
  background-color: var(--color-accent);
}
.quote-btn:hover {
  background-color: var(--color-accent-hover);
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
    display: none;
  }
}

@media (max-width: 576px) {
  .products-list-grid {
    grid-template-columns: 1fr;
  }
}
</style>
