<script setup>
import { ref } from 'vue'
import { RouterLink, useRoute } from 'vue-router'
import { Menu, X, FileText } from 'lucide-vue-next'
import { isRequestModalOpen } from '@/composables/useModal'

const route = useRoute()
const isMobileMenuOpen = ref(false)

const navLinks = [
  { name: 'Home', path: '/' },
  { name: 'About Us', path: '/about' },
  { name: 'Products', path: '/products' },
  { name: 'Contact Us', path: '/contact' }
]

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const closeMobileMenu = () => {
  isMobileMenuOpen.value = false
}

const openQuotationModal = () => {
  isRequestModalOpen.value = true
  closeMobileMenu()
}

const isActive = (path) => {
  return route.path === path
}
</script>

<template>
  <header class="navbar-header">
    <div class="container navbar-inner">
      
      <!-- Corporate Logo Asset -->
      <RouterLink to="/" class="logo" @click="closeMobileMenu">
        <img src="/images/logo.png" alt="MTN Auto Spare Parts" class="logo-img" />
      </RouterLink>

      <!-- Desktop Navigation Menu -->
      <nav class="nav-menu">
        <RouterLink 
          v-for="link in navLinks" 
          :key="link.path" 
          :to="link.path"
          class="nav-link"
          :class="{ active: isActive(link.path) }"
        >
          {{ link.name }}
        </RouterLink>
      </nav>

      <!-- Call to Action -->
      <div class="nav-actions">
        <button @click="openQuotationModal" class="btn btn-primary quote-btn">
          <FileText size="16" /> REQUEST QUOTATION
        </button>
        <button class="mobile-menu-toggle" @click="toggleMobileMenu" aria-label="Toggle Menu">
          <Menu v-if="!isMobileMenuOpen" size="24" />
          <X v-else size="24" />
        </button>
      </div>

    </div>

    <!-- Mobile Drawer Menu -->
    <Transition name="slide-down">
      <div v-if="isMobileMenuOpen" class="mobile-menu-drawer">
        <div class="mobile-links">
          <RouterLink 
            v-for="link in navLinks" 
            :key="link.path" 
            :to="link.path"
            class="mobile-nav-link"
            :class="{ active: isActive(link.path) }"
            @click="closeMobileMenu"
          >
            {{ link.name }}
          </RouterLink>
          <button @click="openQuotationModal" class="btn btn-primary mobile-quote-btn">
            <FileText size="16" /> REQUEST QUOTATION
          </button>
        </div>
      </div>
    </Transition>
  </header>
</template>

<style scoped>
.navbar-header {
  background-color: var(--color-light);
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
  position: sticky;
  top: 0;
  z-index: 99;
}

.navbar-inner {
  height: 80px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  display: flex;
  align-items: center;
}

.logo-img {
  height: 52px;
  width: auto;
  object-fit: contain;
}

.nav-menu {
  display: flex;
  gap: 32px;
}

.nav-link {
  font-weight: 700;
  font-size: 15px;
  text-transform: uppercase;
  color: var(--color-text-dark);
  position: relative;
  padding: 8px 0;
  transition: var(--transition-smooth);
}

.nav-link:hover {
  color: var(--color-primary);
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 3px;
  background-color: var(--color-primary);
  transition: var(--transition-smooth);
}

.nav-link.active {
  color: var(--color-primary);
}

.nav-link.active::after {
  width: 100%;
}

.nav-actions {
  display: flex;
  align-items: center;
  gap: 16px;
}

.quote-btn {
  padding: 10px 20px;
  font-size: 13px;
}

.mobile-menu-toggle {
  display: none;
  background: none;
  border: none;
  cursor: pointer;
  color: var(--color-text-dark);
}

/* Mobile Menu Drawer */
.mobile-menu-drawer {
  position: absolute;
  top: 80px;
  left: 0;
  width: 100%;
  background-color: var(--color-light);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  border-top: 1px solid var(--color-border);
  padding: 20px;
}

.mobile-links {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.mobile-nav-link {
  font-weight: 700;
  font-size: 16px;
  text-transform: uppercase;
  color: var(--color-text-dark);
  padding: 8px 0;
  border-bottom: 1px solid var(--color-light-surface);
}

.mobile-nav-link.active {
  color: var(--color-primary);
  border-bottom-color: var(--color-primary);
}

.mobile-quote-btn {
  width: 100%;
  margin-top: 8px;
}

/* Transition Animations */
.slide-down-enter-active,
.slide-down-leave-active {
  transition: all 0.3s ease-in-out;
}

.slide-down-enter-from,
.slide-down-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}

@media (max-width: 992px) {
  .nav-menu {
    display: none;
  }
  .quote-btn {
    display: none;
  }
  .mobile-menu-toggle {
    display: block;
  }
}
</style>
