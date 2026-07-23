<script setup>
import { RouterLink } from 'vue-router'
import { isQuoteModalOpen } from '@/composables/useModal'

const openQuoteModal = () => {
  isQuoteModalOpen.value = true
}
</script>

<template>
  <footer class="footer">
    <div class="container footer-inner">
      
      <!-- Col 1: Brand Info -->
      <div class="footer-col">
        <svg viewBox="0 0 250 50" width="200" height="40" class="footer-logo">
          <circle cx="25" cy="25" r="22" fill="#cc2900" />
          <path d="M15,15 L28,15 L28,26 L15,26 Z M28,22 L35,29" stroke="#ffffff" stroke-width="2.5" stroke-linecap="round" fill="none" />
          <circle cx="19" cy="19" r="1.5" fill="#ffffff" />
          <text x="56" y="24" font-family="'Outfit', sans-serif" font-weight="900" font-size="20" letter-spacing="0.5" fill="#ffffff">FRESH CUTS</text>
          <text x="56" y="38" font-family="'Outfit', sans-serif" font-weight="700" font-size="9" letter-spacing="1" fill="#cc2900">MEAT TRADING FZCO</text>
        </svg>
        <p class="footer-desc">
          Supplying premium quality fresh meat, chicken, beef and seafood across the UAE. We serve supermarkets, hotels, restaurants, and wholesale traders with strict cold chain compliance.
        </p>
      </div>

      <!-- Col 2: Navigation Links -->
      <div class="footer-col">
        <h4 class="footer-heading">Navigation</h4>
        <ul class="footer-links">
          <li><RouterLink to="/">Home</RouterLink></li>
          <li><RouterLink to="/about">About Us</RouterLink></li>
          <li><RouterLink to="/products">Our Products</RouterLink></li>
          <li><RouterLink to="/wholesale">Wholesale</RouterLink></li>
          <li><RouterLink to="/quality">Quality Standards</RouterLink></li>
          <li><RouterLink to="/contact">Contact Us</RouterLink></li>
        </ul>
      </div>

      <!-- Col 3: Contact details -->
      <div class="footer-col">
        <h4 class="footer-heading">Get in Touch</h4>
        <ul class="footer-contact-list">
          <li><strong>Office Phone:</strong> <a href="tel:+971501234567">+971 50 123 4567</a></li>
          <li><strong>Email Address:</strong> <a href="mailto:info@freshcutsmeat.ae">info@freshcutsmeat.ae</a></li>
          <li><strong>Corporate Address:</strong> Dubai Food Hub, Warehouse A-12, Dubai, United Arab Emirates</li>
        </ul>
      </div>

      <!-- Col 4: Wholesale CTA -->
      <div class="footer-col">
        <h4 class="footer-heading">Wholesale Solutions</h4>
        <p class="footer-desc">Partner with us for customized bulk orders, hotels, or corporate supply contracts.</p>
        <button @click="openQuoteModal" class="btn btn-primary footer-btn">
          Get Wholesale Quote
        </button>
      </div>

    </div>

    <!-- Bottom copyrights and backlinks -->
    <div class="footer-bottom">
      <div class="container footer-bottom-inner">
        <p class="copyright-text">
          &copy; 2026 Fresh Cuts Meat Trading FZCO. All Rights Reserved. Developed by 
          <a href="https://justrise.bh" target="_blank" rel="noopener" class="developer-link">Just Rise Technologies</a>.
        </p>
        <div class="footer-legal">
          <RouterLink to="/privacy-policy">Privacy Policy</RouterLink> | 
          <RouterLink to="/terms-conditions">Terms & Conditions</RouterLink>
        </div>
      </div>
    </div>

    <!-- WhatsApp Floating Button -->
    <a href="https://wa.me/971501234567" class="whatsapp-float" target="_blank" aria-label="Chat on WhatsApp">
      <svg viewBox="0 0 32 32" width="32" height="32" fill="white">
        <path d="M16 2.5C8.5 2.5 2.5 8.5 2.5 16c0 2.4.6 4.7 1.7 6.7l-2.2 8.1 8.3-2.2c2 .1 4.2 .1 5.7 .1 7.5 0 13.5-6 13.5-13.5S23.5 2.5 16 2.5zm0 24.6c-2 0-3.9-.5-5.6-1.5l-.4-.2-4.1 1.1 1.1-4-.3-.4c-1-1.7-1.6-3.7-1.6-5.8 0-6.2 5.1-11.3 11.3-11.3s11.3 5.1 11.3 11.3-5.1 11.3-11.3 11.3z"/>
        <path d="M21.9 19.3c-.3-.1-1.8-.9-2.1-1-.3-.1-.5-.1-.7.2-.2.3-.8 1-1 1.2-.2.2-.4.2-.7.1-.3-.1-1.3-.5-2.4-1.5-.9-.8-1.5-1.8-1.6-2.1-.1-.3 0-.4.1-.6.1-.1.3-.3.4-.5.1-.2.2-.3.3-.5.1-.2 0-.4 0-.5-.1-.1-.7-1.7-1-2.3-.2-.6-.5-.5-.7-.5h-.6c-.2 0-.6.1-.9.4-.3.3-1.1 1.1-1.1 2.7 0 1.6 1.2 3.1 1.3 3.3.1.2 2.3 3.5 5.5 4.9.8.3 1.4.5 1.9.6.8.3 1.5.2 2.1.1.6-.1 1.8-.7 2.1-1.5.2-.8.2-1.4.1-1.5-.2-.1-.5-.2-.8-.3z"/>
      </svg>
    </a>
  </footer>
</template>

<style scoped>
.footer {
  background-color: var(--color-dark);
  color: white;
  padding-top: 60px;
  border-top: 4px solid var(--color-primary);
  position: relative;
}

.footer-inner {
  display: grid;
  grid-template-columns: 2fr 1fr 1.5fr 1.5fr;
  gap: 40px;
  margin-bottom: 40px;
}

.footer-logo {
  margin-bottom: 20px;
}

.footer-heading {
  font-size: 16px;
  font-weight: 800;
  text-transform: uppercase;
  margin-bottom: 24px;
  color: white;
  position: relative;
  padding-bottom: 8px;
}

.footer-heading::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 30px;
  height: 2px;
  background-color: var(--color-accent);
}

.footer-desc {
  font-size: 14px;
  color: var(--color-text-light);
  line-height: 1.6;
}

.footer-links li {
  margin-bottom: 12px;
}

.footer-links a {
  font-size: 14px;
  color: var(--color-text-light);
  transition: var(--transition-smooth);
}

.footer-links a:hover {
  color: var(--color-accent);
  padding-left: 4px;
}

.footer-contact-list li {
  font-size: 14px;
  color: var(--color-text-light);
  line-height: 1.6;
  margin-bottom: 14px;
}

.footer-contact-list a {
  transition: var(--transition-smooth);
}

.footer-contact-list a:hover {
  color: var(--color-accent);
}

.footer-btn {
  width: 100%;
  margin-top: 16px;
  padding: 10px 20px;
  background-color: var(--color-accent);
}

.footer-btn:hover {
  background-color: var(--color-accent-hover);
}

.footer-bottom {
  background-color: #050608;
  padding: 24px 0;
  border-top: 1px solid rgba(255, 255, 255, 0.05);
}

.footer-bottom-inner {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 16px;
}

.copyright-text {
  font-size: 13px;
  color: var(--color-text-light);
}

.developer-link {
  color: var(--color-accent);
  font-weight: 700;
  transition: var(--transition-smooth);
}

.developer-link:hover {
  color: white;
  text-decoration: underline;
}

.footer-legal {
  font-size: 13px;
  color: var(--color-text-light);
}

.footer-legal a {
  transition: var(--transition-smooth);
}

.footer-legal a:hover {
  color: var(--color-accent);
}

/* WhatsApp Floating Button */
.whatsapp-float {
  position: fixed;
  bottom: 30px;
  right: 30px;
  width: 60px;
  height: 60px;
  background-color: #25d366;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 10px rgba(0,0,0,0.3);
  z-index: 998;
  transition: transform 0.3s ease;
}

.whatsapp-float:hover {
  transform: scale(1.1);
}

@media (max-width: 992px) {
  .footer-inner {
    grid-template-columns: 1fr 1fr;
  }
}

@media (max-width: 576px) {
  .footer-inner {
    grid-template-columns: 1fr;
    gap: 30px;
  }
  .footer-bottom-inner {
    flex-direction: column;
    text-align: center;
  }
}
</style>
