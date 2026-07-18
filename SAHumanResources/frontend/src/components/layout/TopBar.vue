<script setup>
import { Phone, Mail, Facebook, Linkedin, Instagram } from 'lucide-vue-next'
</script>

<template>
  <div class="topbar">
    <div class="container topbar-inner">
      <div class="topbar-contact">
        <a href="tel:+971509390051" class="contact-item">
          <Phone size="14" />
          <span>+971 509390051</span>
        </a>
        <a href="tel:+971507648860" class="contact-item">
          <Phone size="14" />
          <span>+971 507648860</span>
        </a>
        <a href="mailto:info@shajadhrconsultancy.com" class="contact-item">
          <Mail size="14" />
          <span>info@shajadhrconsultancy.com</span>
        </a>
      </div>
      <div class="topbar-social">
        <span>Follow Us:</span>
        <a href="#" aria-label="Facebook"><Facebook size="16" /></a>
        <a href="#" aria-label="LinkedIn"><Linkedin size="16" /></a>
        <a href="#" aria-label="Instagram"><Instagram size="16" /></a>
      </div>
    </div>
  </div>
</template>

<style scoped>
.topbar {
  background-color: #f8fcf8;
  color: var(--color-text-main);
  padding: 8px 0;
  font-size: 13px;
  border-bottom: 1px solid var(--color-border);
}

.topbar-inner {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 12px;
}

.topbar-contact {
  display: flex;
  gap: 20px;
  flex-wrap: wrap;
}

.contact-item {
  display: flex;
  align-items: center;
  gap: 6px;
  font-weight: 500;
}

.contact-item:hover {
  color: var(--color-accent);
}

.topbar-social {
  display: flex;
  align-items: center;
  gap: 12px;
  font-weight: 600;
}

.topbar-social a {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 26px;
  height: 26px;
  background-color: var(--color-text-main);
  color: white;
  border-radius: 50%;
  transition: background-color 0.3s;
}

.topbar-social a:hover {
  background-color: var(--color-accent);
}

@media (max-width: 768px) {
  .topbar-inner {
    flex-direction: column;
    justify-content: center;
    text-align: center;
  }
  .topbar-contact {
    justify-content: center;
  }
}
</style>
