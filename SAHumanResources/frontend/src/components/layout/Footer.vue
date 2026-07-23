<script setup>
import { RouterLink } from 'vue-router'
import { MapPin, Phone, Mail, Facebook, Linkedin, Instagram } from 'lucide-vue-next'
</script>

<template>
  <footer class="footer">
    <div class="container footer-inner">
      <div class="footer-col">
        <div class="logo">
          <RouterLink to="/">
            <img src="/logo.png" alt="SHAJAD AHMAD HR CONSULTANCIES" class="logo-img footer-logo" />
          </RouterLink>
        </div>
        <p class="footer-desc">
          Your trusted manpower supply and HR consultancy partner for construction and fit-out projects across UAE.
        </p>
        <div class="social-links">
          <a href="#" aria-label="Facebook"><Facebook size="18" /></a>
          <a href="#" aria-label="LinkedIn"><Linkedin size="18" /></a>
          <a href="#" aria-label="Instagram"><Instagram size="18" /></a>
        </div>
      </div>
      
      <div class="footer-col">
        <h4 class="footer-heading">QUICK LINKS</h4>
        <ul class="footer-links">
          <li><RouterLink to="/">Home</RouterLink></li>
          <li><RouterLink to="/about">About Us</RouterLink></li>
          <li><RouterLink to="/industries">Industries</RouterLink></li>
          <li><RouterLink to="/contact">Contact Us</RouterLink></li>
        </ul>
      </div>

      <div class="footer-col">
        <h4 class="footer-heading">INDUSTRIES WE SERVE</h4>
        <ul class="footer-links">
          <li><RouterLink to="/industries">Construction</RouterLink></li>
          <li><RouterLink to="/industries">Fit Out</RouterLink></li>
          <li><RouterLink to="/industries">MEP</RouterLink></li>
          <li><RouterLink to="/industries">Building Maintenance</RouterLink></li>
          <li><RouterLink to="/industries">Facility Management</RouterLink></li>
        </ul>
      </div>

      <div class="footer-col">
        <h4 class="footer-heading">CONTACT US</h4>
        <ul class="footer-contact">
          <li>
            <MapPin size="16" class="contact-icon" />
            <div>
              <strong>Corporate Office:</strong><br>
              Shajad Ahmad HR Consultancies L.L.C<br>
              Sharjah, UAE
            </div>
          </li>
          <li>
            <Phone size="16" class="contact-icon" />
            <div>
              <a href="tel:+971509390051">+971 509390051</a> | 
              <a href="tel:+971507648860">+971 507648860</a>
            </div>
          </li>
          <li>
            <Mail size="16" class="contact-icon" />
            <a href="mailto:info@shajadhrconsultancy.com">info@shajadhrconsultancy.com</a>
          </li>
        </ul>
      </div>
    </div>
    
    <div class="footer-bottom">
      <div class="container footer-bottom-inner">
        <p>&copy; 2026 Shajad Ahmad Human Resources Consultancies L.L.C. All Rights Reserved. Developed by <a href="https://justrise.bh" target="_blank" rel="noopener" class="developer-link">Just Rise Technologies</a>.</p>
        <div class="footer-legal">
          <RouterLink to="/privacy-policy">Privacy Policy</RouterLink> | 
          <RouterLink to="/terms-conditions">Terms & Conditions</RouterLink>
        </div>
      </div>
    </div>

    <!-- WhatsApp Floating Button -->
    <a href="https://wa.me/971509390051" class="whatsapp-float" target="_blank" aria-label="Chat on WhatsApp">
      <svg viewBox="0 0 32 32" width="32" height="32" fill="white">
        <path d="M16 2.5C8.5 2.5 2.5 8.5 2.5 16c0 2.4.6 4.7 1.7 6.7l-2.2 8.1 8.3-2.2c2 .1 4.2 .1 5.7 .1 7.5 0 13.5-6 13.5-13.5S23.5 2.5 16 2.5zm0 24.6c-2 0-3.9-.5-5.6-1.5l-.4-.2-4.1 1.1 1.1-4-.3-.4c-1-1.7-1.6-3.7-1.6-5.8 0-6.2 5.1-11.3 11.3-11.3s11.3 5.1 11.3 11.3-5.1 11.3-11.3 11.3z"/>
        <path d="M21.9 19.3c-.3-.1-1.8-.9-2.1-1-.3-.1-.5-.1-.7.2-.2.3-.8 1-1 1.2-.2.2-.4.2-.7.1-.3-.1-1.3-.5-2.4-1.5-.9-.8-1.5-1.8-1.6-2.1-.1-.3 0-.4.1-.6.1-.1.3-.3.4-.5.1-.2.2-.3.3-.5.1-.2 0-.4 0-.5-.1-.1-.7-1.7-1-2.3-.2-.6-.5-.5-.7-.5h-.6c-.2 0-.6.1-.9.4-.3.3-1.1 1.1-1.1 2.7 0 1.6 1.2 3.1 1.3 3.3.1.2 2.3 3.5 5.5 4.9.8.3 1.4.5 1.9.6.8.3 1.5.2 2.1.1.6-.1 1.8-.7 2.1-1.5.2-.8.2-1.4.1-1.5-.2-.1-.5-.2-.8-.3z"/>
      </svg>
    </a>
  </footer>
</template>

<style scoped>
.footer {
  background-color: var(--color-primary-dark);
  color: white;
  padding-top: 60px;
}

.footer-inner {
  display: grid;
  grid-template-columns: 2fr 1fr 1.5fr 1.5fr;
  gap: 40px;
  margin-bottom: 40px;
}

.logo {
  margin-bottom: 20px;
}

.footer-logo {
  height: 70px;
  width: auto;
  object-fit: contain;
  background-color: white; /* Ensures it is visible on the dark footer background */
  padding: 8px;
  border-radius: var(--border-radius-sm);
}

.footer-desc {
  font-size: 14px;
  color: #cccccc;
  margin-bottom: 20px;
  max-width: 300px;
}

.social-links {
  display: flex;
  gap: 12px;
}

.social-links a {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 36px;
  height: 36px;
  background-color: white;
  color: var(--color-primary-dark);
  border-radius: 50%;
  transition: all 0.3s ease;
}

.social-links a:hover {
  background-color: var(--color-accent);
  color: white;
}

.footer-heading {
  font-size: 16px;
  font-weight: 700;
  margin-bottom: 20px;
  color: white;
}

.footer-links li {
  margin-bottom: 12px;
}

.footer-links a {
  font-size: 14px;
  color: #cccccc;
  transition: color 0.3s ease;
}

.footer-links a:hover {
  color: var(--color-accent);
}

.footer-contact li {
  display: flex;
  gap: 10px;
  margin-bottom: 16px;
  font-size: 14px;
  color: #cccccc;
}

.contact-icon {
  flex-shrink: 0;
  color: var(--color-accent);
  margin-top: 2px;
}

.footer-bottom {
  background-color: #00260e;
  padding: 20px 0;
  font-size: 12px;
  color: #999999;
}

.footer-bottom-inner {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 10px;
}

.footer-legal a {
  transition: color 0.3s;
}

.footer-legal a:hover {
  color: white;
}

.whatsapp-float {
  position: fixed;
  bottom: 20px;
  right: 20px;
  width: 60px;
  height: 60px;
  background-color: #25d366;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 10px rgba(0,0,0,0.3);
  z-index: 1000;
  transition: transform 0.3s ease;
}

.whatsapp-float:hover {
  transform: scale(1.1);
}

.developer-link {
  color: var(--color-accent, #c9a054);
  text-decoration: none;
  font-weight: 700;
  transition: color 0.3s ease;
}

.developer-link:hover {
  color: white;
  text-decoration: underline;
}

@media (max-width: 992px) {
  .footer-inner {
    grid-template-columns: 1fr 1fr;
  }
}

@media (max-width: 576px) {
  .footer-inner {
    grid-template-columns: 1fr;
  }
  .footer-bottom-inner {
    flex-direction: column;
    text-align: center;
    justify-content: center;
  }
}
</style>
