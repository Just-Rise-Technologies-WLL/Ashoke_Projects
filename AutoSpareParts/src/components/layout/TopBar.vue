<script setup>
import { Phone, Mail, Globe } from 'lucide-vue-next'
</script>

<template>
  <div class="top-bar">
    <div class="container top-bar-inner">
      <div class="top-bar-left">
        <span class="welcome-text">Your Trusted Auto Parts Partner in UAE</span>
      </div>
      <div class="top-bar-right">
        <a href="tel:+971556120923" class="contact-link">
          <Phone size="14" /> <span>+971 556 120 923</span>
        </a>
        <a href="tel:+971045769139" class="contact-link">
          <Phone size="14" /> <span>+971 (04) 576 9139</span>
        </a>
        <a href="mailto:info@mtnautospareparts.com" class="contact-link">
          <Mail size="14" /> <span>info@mtnautospareparts.com</span>
        </a>
        <a href="https://www.mtnautospareparts.com" target="_blank" class="contact-link">
          <Globe size="14" /> <span>www.mtnautospareparts.com</span>
        </a>
      </div>
    </div>
  </div>
</template>

<style scoped>
.top-bar {
  background-color: var(--color-dark);
  color: white;
  padding: 8px 0;
  font-size: 13px;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  z-index: 100;
  position: relative;
}

.top-bar-inner {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.welcome-text {
  color: var(--color-text-light);
  font-weight: 500;
}

.top-bar-right {
  display: flex;
  gap: 20px;
  align-items: center;
  flex-wrap: wrap;
}

.contact-link {
  display: flex;
  align-items: center;
  gap: 6px;
  color: var(--color-text-light);
  transition: var(--transition-smooth);
}

.contact-link:hover {
  color: var(--color-primary);
}

@media (max-width: 992px) {
  .top-bar-inner {
    flex-direction: column;
    gap: 8px;
    text-align: center;
  }
  .top-bar-right {
    justify-content: center;
    gap: 12px;
  }
}
</style>
