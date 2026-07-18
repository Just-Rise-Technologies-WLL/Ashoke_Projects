<script setup>
import { ref } from 'vue'
import { RouterLink } from 'vue-router'
import { Menu, X, UserSearch } from 'lucide-vue-next'
import Button from '../ui/Button.vue'
import { isRequestModalOpen } from '@/composables/useModal'

const isMobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const openModal = () => {
  isRequestModalOpen.value = true
  if (isMobileMenuOpen.value) toggleMobileMenu()
}
</script>

<template>
  <nav class="navbar">
    <div class="container navbar-inner">
      <!-- Logo using image -->
      <RouterLink to="/" class="logo">
        <img src="/logo.png" alt="SHAJAD AHMAD HR CONSULTANCIES" class="logo-img" />
      </RouterLink>

      <!-- Desktop Navigation -->
      <div class="nav-links desktop-only">
        <RouterLink to="/" class="nav-item">HOME</RouterLink>
        <RouterLink to="/about" class="nav-item">ABOUT US</RouterLink>
        <RouterLink to="/industries" class="nav-item">INDUSTRIES</RouterLink>
        <RouterLink to="/contact" class="nav-item">CONTACT US</RouterLink>
      </div>

      <div class="nav-actions desktop-only">
        <Button @click="openModal" variant="primary" :icon="true">
          <UserSearch size="18" /> REQUEST MANPOWER
        </Button>
      </div>

      <!-- Mobile Menu Toggle -->
      <button class="mobile-toggle hide-desktop" @click="toggleMobileMenu">
        <Menu v-if="!isMobileMenuOpen" size="28" />
        <X v-else size="28" />
      </button>

      <!-- Mobile Navigation -->
      <div class="mobile-menu" :class="{ 'is-open': isMobileMenuOpen }">
        <RouterLink to="/" class="mobile-nav-item" @click="toggleMobileMenu">HOME</RouterLink>
        <RouterLink to="/about" class="mobile-nav-item" @click="toggleMobileMenu">ABOUT US</RouterLink>
        <RouterLink to="/industries" class="mobile-nav-item" @click="toggleMobileMenu">INDUSTRIES</RouterLink>
        <RouterLink to="/contact" class="mobile-nav-item" @click="toggleMobileMenu">CONTACT US</RouterLink>
        <div class="mobile-actions">
          <Button @click="openModal" variant="primary">REQUEST MANPOWER</Button>
        </div>
      </div>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  background-color: white;
  box-shadow: var(--shadow-sm);
  position: sticky;
  top: 0;
  z-index: 1000;
}

.navbar-inner {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 80px;
}

.logo {
  display: flex;
  align-items: center;
}

.logo-img {
  height: 60px;
  width: auto;
  object-fit: contain;
}

.nav-links {
  display: flex;
  gap: 30px;
}

.nav-item {
  font-weight: 700;
  font-size: 14px;
  color: var(--color-primary);
  text-transform: uppercase;
  padding: 10px 0;
  position: relative;
}

.nav-item::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 2px;
  background-color: var(--color-accent);
  transition: width 0.3s ease;
}

.nav-item:hover::after,
.nav-item.router-link-active::after {
  width: 100%;
}

.mobile-toggle {
  background: none;
  border: none;
  color: var(--color-primary);
}

.mobile-menu {
  display: none;
}

.hide-desktop {
  display: none;
}

@media (max-width: 992px) {
  .desktop-only {
    display: none;
  }

  .hide-desktop {
    display: block;
  }

  .mobile-menu {
    display: flex;
    flex-direction: column;
    position: absolute;
    top: 80px;
    left: 0;
    width: 100%;
    background-color: white;
    box-shadow: var(--shadow-md);
    padding: 20px;
    transform: translateY(-100%);
    opacity: 0;
    pointer-events: none;
    transition: all 0.3s ease;
  }

  .mobile-menu.is-open {
    transform: translateY(0);
    opacity: 1;
    pointer-events: auto;
  }

  .mobile-nav-item {
    padding: 15px 0;
    font-weight: 600;
    color: var(--color-primary);
    border-bottom: 1px solid var(--color-border);
  }

  .mobile-actions {
    margin-top: 20px;
  }
}
</style>
