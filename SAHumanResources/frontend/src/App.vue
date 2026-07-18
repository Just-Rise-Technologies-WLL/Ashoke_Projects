<script setup>
import { RouterView } from 'vue-router'
import RequestModal from '@/components/ui/RequestModal.vue'
</script>

<template>
  <RouterView />
  <RequestModal />
</template>

<style>
/* App level unstructured styles if needed, mostly handled in main.css */
#app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
</style>
