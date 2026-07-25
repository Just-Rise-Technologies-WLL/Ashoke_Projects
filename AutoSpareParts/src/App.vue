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
        <!-- Pulsing corporate logo image -->
        <img src="/images/logo.png" alt="MTN Auto Spare Parts" class="loader-logo" />
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
/* Preloader Overlay */
.preloader {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: #0a0b0d; /* Matching dark theme */
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
  height: 80px;
  width: auto;
  object-fit: contain;
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
  background-color: #dc2626; /* Brand Red */
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
