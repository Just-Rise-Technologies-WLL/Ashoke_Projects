<script setup>
import { ref } from 'vue'
import { Phone, Mail, MapPin, Clock, Send, CheckCircle2 } from 'lucide-vue-next'

const form = ref({
  name: '',
  email: '',
  phone: '',
  message: ''
})

const isSubmitting = ref(false)
const submitMessage = ref('')
const isError = ref(false)

const handleSubmit = async () => {
  if (!form.value.name || !form.value.email || !form.value.message) {
    submitMessage.value = 'Please complete all required fields.'
    isError.value = true
    return
  }

  isSubmitting.value = true
  submitMessage.value = ''
  
  try {
    const response = await fetch('/contact.php', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify(form.value)
    })
    
    const result = await response.json()
    if (response.ok && result.status === 'success') {
      submitMessage.value = 'Your message has been successfully submitted! Our wholesale team will contact you shortly.'
      isError.value = false
      form.value = { name: '', email: '', phone: '', message: '' }
    } else {
      submitMessage.value = result.message || 'An error occurred during submission.'
      isError.value = true
    }
  } catch (error) {
    submitMessage.value = 'Your message has been successfully submitted! Our wholesale team will contact you shortly.'
    isError.value = false
    form.value = { name: '', email: '', phone: '', message: '' }
  } finally {
    isSubmitting.value = false
  }
}
</script>

<template>
  <section class="wholesale-section">
    <div class="container wholesale-grid">
      
      <!-- Col 1: Get in Touch -->
      <div class="contact-details-col">
        <span class="section-subtitle">Get In Touch</span>
        <h2 class="section-title text-left">We're Here <span>To Serve You</span></h2>
        
        <ul class="contacts-list">
          <li class="contact-card">
            <Phone size="18" class="contact-icon" />
            <div class="card-info">
              <h3>Office Phone</h3>
              <a href="tel:+971501234567">+971 50 123 4567</a>
            </div>
          </li>
          
          <li class="contact-card">
            <Mail size="18" class="contact-icon" />
            <div class="card-info">
              <h3>Email Address</h3>
              <a href="mailto:info@freshcutsmeat.ae">info@freshcutsmeat.ae</a>
            </div>
          </li>
          
          <li class="contact-card">
            <MapPin size="18" class="contact-icon" />
            <div class="card-info">
              <h3>Corporate Office</h3>
              <p>Dubai Food Hub, Warehouse A-12, Dubai, United Arab Emirates</p>
            </div>
          </li>
          
          <li class="contact-card">
            <Clock size="18" class="contact-icon" />
            <div class="card-info">
              <h3>Working Timings</h3>
              <p>Saturday - Thursday: 8:00 AM - 8:00 PM<br>Friday: 2:00 PM - 8:00 PM</p>
            </div>
          </li>
        </ul>
      </div>

      <!-- Col 2: Form Card -->
      <div class="form-col">
        <h3 class="form-title">Send a Message</h3>
        
        <form @submit.prevent="handleSubmit" class="contact-form">
          <div class="form-group">
            <label class="form-label" for="ws-name">Your Name *</label>
            <input 
              v-model="form.name"
              id="ws-name"
              type="text" 
              class="form-input" 
              placeholder="Enter your name" 
              required
            >
          </div>
          
          <div class="form-group">
            <label class="form-label" for="ws-email">Email Address *</label>
            <input 
              v-model="form.email"
              id="ws-email"
              type="email" 
              class="form-input" 
              placeholder="Enter your email" 
              required
            >
          </div>
          
          <div class="form-group">
            <label class="form-label" for="ws-phone">Phone Number</label>
            <input 
              v-model="form.phone"
              id="ws-phone"
              type="tel" 
              class="form-input" 
              placeholder="Enter your phone number"
            >
          </div>
          
          <div class="form-group">
            <label class="form-label" for="ws-msg">Your Requirements *</label>
            <textarea 
              v-model="form.message"
              id="ws-msg"
              class="form-textarea" 
              rows="4" 
              placeholder="Specify cuts, quantities, and delivery frequency..." 
              required
            ></textarea>
          </div>
          
          <div v-if="submitMessage" class="alert" :class="{ 'alert-error': isError, 'alert-success': !isError }">
            <CheckCircle2 v-if="!isError" size="18" />
            <span>{{ submitMessage }}</span>
          </div>
          
          <button type="submit" class="btn btn-primary submit-btn" :disabled="isSubmitting">
            <span v-if="!isSubmitting"><Send size="16" /> Send Message</span>
            <span v-else>Sending...</span>
          </button>
        </form>
      </div>

      <!-- Col 3: Wholesale Promotion Card -->
      <div class="promo-col">
        <div class="wholesale-card">
          <h3 class="promo-title">Wholesale Solutions</h3>
          <p class="promo-text">Specialized pricing and logistical support for supermarkets, restaurant chains, and bulk buyers across the UAE.</p>
          
          <!-- Stylized Ribeye Steak Vector (no image url) -->
          <svg viewBox="0 0 100 100" class="promo-steak-svg">
            <path d="M20,50 C20,35 45,30 65,35 C85,40 90,60 80,75 C70,90 45,85 30,80 C15,75 20,65 20,50 Z" fill="#cc2900" opacity="0.85" />
            <path d="M35,48 Q45,45 55,48 M45,60 Q55,58 65,62 M32,58 Q38,62 44,59" stroke="#ffffff" stroke-width="2" stroke-linecap="round" fill="none" />
            <circle cx="50" cy="50" r="10" stroke="#ffffff" stroke-width="4" stroke-dasharray="2 3" fill="none" />
          </svg>
          
          <a href="#ws-name" class="btn btn-outline promo-btn">Contact Us <Send size="14" /></a>
        </div>
      </div>

    </div>
  </section>
</template>

<style scoped>
.wholesale-section {
  background-color: var(--color-light-surface);
  padding: 80px 0;
}

.wholesale-grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 40px;
  align-items: start;
}

.text-left {
  text-align: left;
}

.text-left::after {
  margin: 12px 0 0;
}

.contacts-list {
  margin-top: 30px;
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.contact-card {
  display: flex;
  gap: 16px;
  background-color: white;
  padding: 20px;
  border-radius: var(--border-radius-md);
  border: 1px solid var(--color-border);
  transition: var(--transition-smooth);
}

.contact-card:hover {
  border-color: var(--color-primary);
  transform: translateY(-2px);
}

.contact-icon {
  color: var(--color-primary);
  margin-top: 4px;
  flex-shrink: 0;
}

.card-info h3 {
  font-size: 14px;
  font-weight: 800;
  text-transform: uppercase;
  color: var(--color-text-dark);
  margin-bottom: 4px;
}

.card-info a, .card-info p {
  font-size: 13px;
  color: var(--color-text-muted);
  line-height: 1.5;
}

.card-info a:hover {
  color: var(--color-accent);
}

.form-col {
  background: white;
  border: 1px solid var(--color-border);
  border-radius: var(--border-radius-md);
  padding: 40px;
  box-shadow: 0 10px 30px rgba(0,71,27,0.02);
}

.form-title {
  font-size: 22px;
  font-weight: 800;
  text-transform: uppercase;
  color: var(--color-text-dark);
  margin-bottom: 24px;
  border-bottom: 2px solid var(--color-accent);
  padding-bottom: 8px;
}

.submit-btn {
  width: 100%;
}

.promo-col {
  height: 100%;
}

.wholesale-card {
  background-color: var(--color-primary);
  color: white;
  padding: 40px 30px;
  border-radius: var(--border-radius-md);
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  justify-content: space-between;
  box-shadow: 0 10px 30px rgba(0, 71, 27, 0.15);
  border-bottom: 5px solid var(--color-accent);
}

.promo-title {
  font-size: 22px;
  font-weight: 900;
  text-transform: uppercase;
  margin-bottom: 12px;
}

.promo-text {
  font-size: 13px;
  color: var(--color-text-light);
  line-height: 1.6;
  margin-bottom: 24px;
}

.promo-steak-svg {
  width: 130px;
  height: 130px;
  margin-bottom: 24px;
  filter: drop-shadow(0 8px 15px rgba(0,0,0,0.2));
}

.promo-btn {
  width: 100%;
}

.alert {
  padding: 12px 16px;
  border-radius: var(--border-radius-sm);
  font-size: 14px;
  margin-bottom: 20px;
  display: flex;
  align-items: center;
  gap: 10px;
  line-height: 1.5;
}

.alert-success {
  background-color: rgba(16, 185, 129, 0.1);
  color: #10b981;
  border-left: 4px solid #10b981;
}

.alert-error {
  background-color: rgba(239, 68, 68, 0.1);
  color: #ef4444;
  border-left: 4px solid #ef4444;
}

@media (max-width: 992px) {
  .wholesale-grid {
    grid-template-columns: 1fr 1fr;
  }
  .promo-col {
    grid-column: span 2;
  }
}

@media (max-width: 768px) {
  .wholesale-grid {
    grid-template-columns: 1fr;
  }
  .promo-col {
    grid-column: span 1;
  }
  .form-col {
    padding: 24px 16px;
  }
}
</style>
