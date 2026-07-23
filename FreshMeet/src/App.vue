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
        <!-- SVG Pulsing Butcher badge representing Fresh Cuts -->
        <svg viewBox="0 0 100 100" width="80" height="80" class="loader-logo">
          <circle cx="50" cy="50" r="40" fill="#cc2900" />
          <path d="M30,30 L56,30 L56,52 L30,52 Z M56,44 L70,58" stroke="#ffffff" stroke-width="5" stroke-linecap="round" fill="none" />
          <circle cx="38" cy="38" r="3" fill="#ffffff" />
        </svg>
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
  background-color: #0a0c10;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 9999;
}

.loader-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 24px;
}

.loader-logo {
  animation: pulseLogo 1.5s ease-in-out infinite;
}

.loader-bar {
  width: 120px;
  height: 3px;
  background-color: rgba(255, 255, 255, 0.05);
  border-radius: 10px;
  overflow: hidden;
  position: relative;
}

.loader-progress {
  width: 40px;
  height: 100%;
  background-color: #cc2900; /* Flame Red */
  border-radius: 10px;
  position: absolute;
  left: -40px;
  animation: loadingBar 1.2s cubic-bezier(0.4, 0, 0.2, 1) infinite;
}

@keyframes pulseLogo {
  0%, 100% {
    transform: scale(1);
    opacity: 0.8;
  }
  50% {
    transform: scale(1.08);
    opacity: 1;
  }
}

@keyframes loadingBar {
  0% {
    left: -40px;
  }
  100% {
    left: 120px;
  }
}

/* Page transitions */
.fade-leave-active {
  transition: opacity 0.5s ease;
}
.fade-leave-to {
  opacity: 0;
}
</style>
