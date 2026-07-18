<script setup>
import { ArrowRight, PhoneCall, HardHat } from 'lucide-vue-next'
import Button from '../ui/Button.vue'
import { isRequestModalOpen } from '@/composables/useModal'

const openModal = () => {
  isRequestModalOpen.value = true
}
</script>

<template>
  <section class="cta-banner">
    <div class="container cta-container">
      <div class="cta-left">
        <div class="cta-icon-wrap">
          <HardHat size="40" class="cta-icon" />
        </div>
        <div class="cta-text">
          <h2>NEED SKILLED WORKERS<br/>FOR YOUR NEXT PROJECT?</h2>
          <p>Our team is ready to support your manpower requirements.</p>
        </div>
      </div>
      
      <div class="cta-right">
        <Button @click="openModal" variant="primary" class="cta-btn-primary">
          REQUEST MANPOWER NOW <ArrowRight size="16" />
        </Button>
        <Button to="tel:+971509390051" variant="outline" class="cta-btn-outline">
          <PhoneCall size="16" /> CALL US NOW
        </Button>
      </div>
    </div>
  </section>
</template>

<style scoped>
.cta-banner {
  background-color: var(--color-primary-dark);
  padding: 40px 0;
  margin-bottom: -1px; /* Align with footer */
}

.cta-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 30px;
}

.cta-left {
  display: flex;
  align-items: center;
  gap: 25px;
}

.cta-icon-wrap {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  background-color: var(--color-accent);
  display: flex;
  align-items: center;
  justify-content: center;
}

.cta-icon {
  color: white;
}

.cta-text h2 {
  color: white;
  font-size: 28px;
  font-weight: 800;
  line-height: 1.2;
  margin-bottom: 8px;
}

.cta-text p {
  color: #eeeeee;
  font-size: 15px;
}

.cta-right {
  display: flex;
  gap: 15px;
  flex-wrap: wrap;
}

/* Specific styling to match the screenshot */
:deep(.cta-btn-primary) {
  background-color: var(--color-accent);
  color: white;
}
:deep(.cta-btn-primary:hover) {
  background-color: var(--color-accent-dark);
}
:deep(.cta-btn-outline) {
  border-color: white;
  color: white;
}
:deep(.cta-btn-outline:hover) {
  background-color: rgba(255,255,255,0.1);
  color: white;
}

@media (max-width: 992px) {
  .cta-container {
    flex-direction: column;
    text-align: center;
  }
  .cta-left {
    flex-direction: column;
  }
  .cta-right {
    justify-content: center;
  }
}
</style>
