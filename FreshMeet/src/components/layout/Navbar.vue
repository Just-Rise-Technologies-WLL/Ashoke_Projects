<script setup>
import { ref } from 'vue'
import { RouterLink, useRoute } from 'vue-router'
import { Menu, X, UtensilsCrossed } from 'lucide-vue-next'
import { isQuoteModalOpen } from '@/composables/useModal'

const route = useRoute()
const isMobileMenuOpen = ref(false)

const navLinks = [
  { name: 'Home', path: '/' },
  { name: 'About Us', path: '/about' },
  { name: 'Products', path: '/products' },
  { name: 'Wholesale', path: '/wholesale' },
  { name: 'Quality', path: '/quality' },
  { name: 'Contact Us', path: '/contact' }
]

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const closeMobileMenu = () => {
  isMobileMenuOpen.value = false
}

const openQuoteModal = () => {
  isQuoteModalOpen.value = true
  closeMobileMenu()
}

const isActive = (path) => {
  return route.path === path
}
</script>

<template>
  <header class="navbar-header">
    <div class="container navbar-inner">
      
      <!-- Premium SVG Logo for Fresh Cuts -->
      <RouterLink to="/" class="logo" @click="closeMobileMenu">
        <svg viewBox="0 0 250 50" width="200" height="40" class="logo-svg">
          <!-- Butcher Cleaver circular badge -->
          <circle cx="25" cy="25" r="22" fill="#cc2900" />
          <!-- Cleaver drawing -->
          <path d="M15,15 L28,15 L28,26 L15,26 Z M28,22 L35,29" stroke="#ffffff" stroke-width="2.5" stroke-linecap="round" fill="none" />
          <circle cx="19" cy="19" r="1.5" fill="#ffffff" />
          
          <!-- Brand text -->
          <text x="56" y="24" font-family="'Outfit', sans-serif" font-weight="900" font-size="20" letter-spacing="0.5" fill="#ffffff">FRESH CUTS</text>
          <text x="56" y="38" font-family="'Outfit', sans-serif" font-weight="700" font-size="9" letter-spacing="1" fill="#cc2900">MEAT TRADING FZCO</text>
        </svg>
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

      <!-- CTA -->
      <div class="nav-actions">
        <button @click="openQuoteModal" class="btn btn-primary quote-btn">
          <UtensilsCrossed size="16" /> Get A Quote
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
          <button @click="openQuoteModal" class="btn btn-primary mobile-quote-btn">
            <UtensilsCrossed size="16" /> Get A Quote
          </button>
        </div>
      </div>
    </Transition>
  </header>
</template>

<style scoped>
.navbar-header {
  background-color: var(--color-dark);
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
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

.nav-menu {
  display: flex;
  gap: 28px;
}

.nav-link {
  font-weight: 700;
  font-size: 14px;
  text-transform: uppercase;
  color: #ffffff;
  position: relative;
  padding: 8px 0;
  transition: var(--transition-smooth);
}

.nav-link:hover {
  color: var(--color-accent);
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 3px;
  background-color: var(--color-accent);
  transition: var(--transition-smooth);
}

.nav-link.active {
  color: var(--color-accent);
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
  background-color: var(--color-accent);
}

.mobile-menu-toggle {
  display: none;
  background: none;
  border: none;
  cursor: pointer;
  color: #ffffff;
}

/* Mobile Menu Drawer */
.mobile-menu-drawer {
  position: absolute;
  top: 80px;
  left: 0;
  width: 100%;
  background-color: var(--color-dark);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
  border-top: 1px solid rgba(255, 255, 255, 0.05);
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
  color: #ffffff;
  padding: 8px 0;
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
}

.mobile-nav-link.active {
  color: var(--color-accent);
  border-bottom-color: var(--color-accent);
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
