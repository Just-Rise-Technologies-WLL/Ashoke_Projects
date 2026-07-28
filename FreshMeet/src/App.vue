<script setup>
import { ref, onMounted } from 'vue'
import { RouterView } from 'vue-router'
import RequestModal from '@/components/ui/RequestModal.vue'

const isLoading = ref(true)

onMounted(() => {
  setTimeout(() => {
    isLoading.value = false
  }, 1000)
})
</script>

<template>
  <Transition name="fade">
    <div v-if="isLoading" class="preloader">
      <div class="loader-content">
        <!-- Official Brand Logo Preloader Card -->
        <div class="logo-loader-badge">
          <img src="/logo.png" alt="Fresh Cuts Meat Trading FZCO Logo" class="loader-logo-img" />
        </div>
        <div class="loader-brand-title">
          <span>FRESH CUTS</span>
          <span class="sub-tag">MEAT TRADING FZCO</span>
        </div>
        <div class="loader-bar">
          <div class="loader-progress"></div>
        </div>
      </div>
    </div>
  </Transition>

  <RouterView />
  <RequestModal />
</template>

<style>
/* Preloader Styles */
.preloader {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: #0c0d0e;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 9999;
}

.loader-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 16px;
}

.logo-loader-badge {
  background: rgba(255, 255, 255, 0.04);
  padding: 16px 28px;
  border-radius: 12px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5), 0 0 20px rgba(204, 41, 0, 0.2);
  backdrop-filter: blur(8px);
  animation: pulseLogo 1.8s ease-in-out infinite;
}

.loader-logo-img {
  height: 48px;
  width: auto;
  object-fit: contain;
  display: block;
}

.loader-brand-title {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2px;
}

.loader-brand-title span:first-child {
  color: #ffffff;
  font-weight: 900;
  font-size: 14px;
  letter-spacing: 2px;
}

.loader-brand-title .sub-tag {
  color: #cc2900;
  font-weight: 800;
  font-size: 10px;
  letter-spacing: 1.5px;
}

.loader-bar {
  width: 140px;
  height: 3px;
  background-color: rgba(255, 255, 255, 0.08);
  border-radius: 10px;
  overflow: hidden;
  position: relative;
  margin-top: 6px;
}

.loader-progress {
  width: 50px;
  height: 100%;
  background: linear-gradient(90deg, #cc2900, #ff4d2d);
  box-shadow: 0 0 8px #cc2900;
  border-radius: 10px;
  position: absolute;
  left: -50px;
  animation: loadingBar 1.2s cubic-bezier(0.4, 0, 0.2, 1) infinite;
}

@keyframes pulseLogo {
  0%, 100% {
    transform: scale(1);
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5), 0 0 20px rgba(204, 41, 0, 0.15);
  }
  50% {
    transform: scale(1.04);
    box-shadow: 0 12px 35px rgba(0, 0, 0, 0.6), 0 0 28px rgba(204, 41, 0, 0.35);
  }
}

@keyframes loadingBar {
  0% {
    left: -50px;
  }
  100% {
    left: 140px;
  }
}

/* Page transitions */
.fade-leave-active {
  transition: opacity 0.4s ease;
}
.fade-leave-to {
  opacity: 0;
}
</style>
