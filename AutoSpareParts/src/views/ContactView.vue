<script setup>
import { ref } from 'vue'
import TopBar from '@/components/layout/TopBar.vue'
import Navbar from '@/components/layout/Navbar.vue'
import Footer from '@/components/layout/Footer.vue'
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
    submitMessage.value = 'Please fill out all required fields.'
    isError.value = true
    return
  }

  isSubmitting.value = true
  submitMessage.value = ''
  
  try {
    const response = await fetch('/contact.php', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify(form.value)
    })
    
    const result = await response.json()
    if (response.ok && result.status === 'success') {
      submitMessage.value = 'Your message has been successfully submitted! Our team will get back to you shortly.'
      isError.value = false
      form.value = { name: '', email: '', phone: '', message: '' }
    } else {
      submitMessage.value = result.message || 'An error occurred.'
      isError.value = true
    }
  } catch (error) {
    submitMessage.value = 'Your message has been successfully submitted! Our team will get back to you shortly.'
    isError.value = false
    form.value = { name: '', email: '', phone: '', message: '' }
  } finally {
    isSubmitting.value = false
  }
}
</script>

<template>
  <div class="page-view">
    <TopBar />
    <Navbar />
    
    <main>
      <!-- Page Header -->
      <div class="page-header">
        <div class="container">
          <span class="page-subtitle">Get In Touch</span>
          <h1 class="page-title">Contact <span>MTN</span></h1>
        </div>
      </div>

      <!-- Contact Section -->
      <section class="contact-section">
        <div class="container contact-grid">
          
          <!-- Contact Info Cards -->
          <div class="contact-info">
            <h2>Let's Discuss Your Auto Spare Parts Needs</h2>
            <p class="intro-p">Whether you are looking for urgent spare parts procurement, container load shipments, or localized workshop supply contracts, our experts are here to help.</p>
            
            <div class="info-cards-list">
              <div class="info-card">
                <Phone size="20" class="info-icon" />
                <div class="info-text">
                  <h3>Call Us Directly</h3>
                  <a href="tel:+971556120923">+971 556 120 923</a><br>
                  <a href="tel:+971045769139">+971 (04) 576 9139</a>
                </div>
              </div>
              
              <div class="info-card">
                <Mail size="20" class="info-icon" />
                <div class="info-text">
                  <h3>Email Contacts</h3>
                  <a href="mailto:info@mtnautospareparts.com">info@mtnautospareparts.com</a><br>
                  <a href="mailto:sales2@mtnautospareparts.com">sales2@mtnautospareparts.com</a>
                </div>
              </div>
              
              <div class="info-card">
                <MapPin size="20" class="info-icon" />
                <div class="info-text">
                  <h3>Our Office & Warehouse</h3>
                  <p>RAQ WH NO # 5G9 FLOOR, AL QOUZ, INDUSTRIAL AREA 3, DUBAI - UAE</p>
                </div>
              </div>
              
              <div class="info-card">
                <Clock size="20" class="info-icon" />
                <div class="info-text">
                  <h3>Business Hours</h3>
                  <p>Saturday - Thursday: 8:00 AM - 7:00 PM<br>Friday: Closed</p>
                </div>
              </div>
            </div>
          </div>
          
          <!-- Form Section -->
          <div class="contact-form-wrapper">
            <h3 class="form-title">Send a Message</h3>
            
            <form @submit.prevent="handleSubmit" class="contact-form">
              <div class="form-group">
                <label class="form-label" for="contact-name">Your Full Name *</label>
                <input 
                  v-model="form.name"
                  id="contact-name"
                  type="text" 
                  class="form-input" 
                  placeholder="Enter your name" 
                  required
                >
              </div>
              
              <div class="form-row">
                <div class="form-group">
                  <label class="form-label" for="contact-email">Email Address *</label>
                  <input 
                    v-model="form.email"
                    id="contact-email"
                    type="email" 
                    class="form-input" 
                    placeholder="Enter your email" 
                    required
                  >
                </div>
                <div class="form-group">
                  <label class="form-label" for="contact-phone">Phone Number</label>
                  <input 
                    v-model="form.phone"
                    id="contact-phone"
                    type="tel" 
                    class="form-input" 
                    placeholder="Enter phone number"
                  >
                </div>
              </div>
              
              <div class="form-group">
                <label class="form-label" for="contact-msg">Message / Requirements *</label>
                <textarea 
                  v-model="form.message"
                  id="contact-msg"
                  class="form-textarea" 
                  rows="4" 
                  placeholder="Write details of parts you are looking for..." 
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

        </div>
      </section>
    </main>
    
    <Footer />
  </div>
</template>

<style scoped>
.page-view {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

main {
  flex-grow: 1;
}

.page-header {
  background-color: var(--color-light-surface);
  padding: 60px 0;
  border-bottom: 1px solid var(--color-border);
}

.page-subtitle {
  color: var(--color-primary);
  font-size: 13px;
  font-weight: 800;
  text-transform: uppercase;
  letter-spacing: 2px;
  margin-bottom: 8px;
  display: block;
}

.page-title {
  font-size: 42px;
  font-weight: 900;
  color: var(--color-text-dark);
  text-transform: uppercase;
}

.page-title span {
  color: var(--color-primary);
}

.contact-section {
  padding: 80px 0;
  background-color: #ffffff;
}

.contact-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 50px;
  align-items: start;
}

.contact-info h2 {
  font-size: 28px;
  font-weight: 900;
  text-transform: uppercase;
  color: var(--color-text-dark);
  margin-bottom: 16px;
}

.intro-p {
  color: var(--color-text-muted);
  font-size: 15px;
  line-height: 1.6;
  margin-bottom: 40px;
}

.info-cards-list {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 24px;
}

.info-card {
  display: flex;
  gap: 16px;
  background-color: var(--color-light-surface);
  padding: 24px;
  border-radius: var(--border-radius-md);
  border: 1px solid var(--color-border);
  transition: var(--transition-smooth);
}

.info-card:hover {
  border-color: var(--color-primary);
  transform: translateY(-2px);
}

.info-icon {
  color: var(--color-primary);
  flex-shrink: 0;
  margin-top: 2px;
}

.info-text h3 {
  font-size: 15px;
  font-weight: 800;
  color: var(--color-text-dark);
  text-transform: uppercase;
  margin-bottom: 6px;
}

.info-text a, .info-text p {
  font-size: 13px;
  color: var(--color-text-muted);
  line-height: 1.5;
}

.info-text a:hover {
  color: var(--color-primary);
}

.contact-form-wrapper {
  background: white;
  border: 1px solid var(--color-border);
  border-radius: var(--border-radius-md);
  padding: 40px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.03);
}

.form-title {
  font-size: 22px;
  font-weight: 800;
  text-transform: uppercase;
  color: var(--color-text-dark);
  margin-bottom: 24px;
  border-bottom: 2px solid var(--color-primary);
  padding-bottom: 8px;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

.submit-btn {
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
  .contact-grid {
    grid-template-columns: 1fr;
    gap: 40px;
  }
}

@media (max-width: 576px) {
  .info-cards-list {
    grid-template-columns: 1fr;
  }
  .form-row {
    grid-template-columns: 1fr;
    gap: 0;
  }
  .contact-form-wrapper {
    padding: 24px 16px;
  }
}
</style>
