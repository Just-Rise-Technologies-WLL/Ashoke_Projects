<script setup>
import { ref, onMounted } from 'vue'
import { RouterView } from 'vue-router'
import RequestModal from '@/components/ui/RequestModal.vue'

const isLoading = ref(true)

onMounted(() => {
  // Give it a brief moment to display before fading out
  setTimeout(() => {
    isLoading.value = false
  }, 1000)
})
</script>

<template>
  <Transition name="fade">
    <div v-if="isLoading" class="preloader">
      <div class="loader-content">
        <img src="/logo.png" alt="Shajad Ahmad Logo" class="loader-logo" />
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
#app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

/* Preloader Styles */
.preloader {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: #ffffff;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 9999;
}

.loader-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
}

.loader-logo {
  height: 70px;
  object-fit: contain;
  animation: pulseLogo 1.5s ease-in-out infinite;
}

.loader-bar {
  width: 140px;
  height: 3px;
  background-color: #f1f5f1;
  border-radius: 10px;
  overflow: hidden;
  position: relative;
}

.loader-progress {
  width: 50px;
  height: 100%;
  background-color: #00471b; /* Brand Dark Green */
  border-radius: 10px;
  position: absolute;
  left: -50px;
  animation: loadingBar 1.2s cubic-bezier(0.4, 0, 0.2, 1) infinite;
}

@keyframes pulseLogo {
  0%, 100% {
    transform: scale(1);
    opacity: 0.85;
  }
  50% {
    transform: scale(1.05);
    opacity: 1;
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

/* Fade Transition */
.fade-leave-active {
  transition: opacity 0.5s ease;
}
.fade-leave-to {
  opacity: 0;
}
</style>
