<script setup>
import { ref } from 'vue'
import TopBar from '@/components/layout/TopBar.vue'
import Navbar from '@/components/layout/Navbar.vue'
import Footer from '@/components/layout/Footer.vue'
import SectionHeader from '@/components/ui/SectionHeader.vue'
import Button from '@/components/ui/Button.vue'
import { MapPin, Phone, Mail, Send } from 'lucide-vue-next'

const form = ref({
  name: '',
  email: '',
  phone: '',
  message: ''
})

const isSubmitting = ref(false)
const submitMessage = ref('')
const isError = ref(false)

const submitForm = async () => {
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
    
    if (result.status === 'success') {
      submitMessage.value = result.message
      isError.value = false
      // Reset form
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
          <SectionHeader subtitle="Get In Touch" title="Contact Us" :centered="false" class="page-title-header" />
        </div>
      </div>

      <section class="contact-section">
        <div class="container contact-container">
          
          <div class="contact-info">
            <h3>Let's Discuss Your Manpower Needs</h3>
            <p class="intro-p">Whether you need a short-term specialized team or a massive long-term workforce, our consultants are ready to assist you rapidly.</p>
            
            <div class="info-cards">
              <div class="info-card">
                <div class="icon-wrap"><MapPin size="24" class="info-icon" /></div>
                <div class="info-content">
                  <h4>Corporate Office</h4>
                  <p>Shajad Ahmad HR Consultancies L.L.C<br/>Sharjah, UAE</p>
                </div>
              </div>
              
              <div class="info-card">
                <div class="icon-wrap"><Phone size="24" class="info-icon" /></div>
                <div class="info-content">
                  <h4>Call Us At</h4>
                  <p><a href="tel:+971509390051">+971 50 939 0051</a><br/>
                     <a href="tel:+971507648860">+971 50 764 8860</a></p>
                </div>
              </div>
              
              <div class="info-card">
                <div class="icon-wrap"><Mail size="24" class="info-icon" /></div>
                <div class="info-content">
                  <h4>Email Us</h4>
                  <p><a href="mailto:info@shajadhrconsultancy.com">info@shajadhrconsultancy.com</a></p>
                </div>
              </div>
            </div>
          </div>
          
          <div class="contact-form-wrapper">
            <h3>Send a Message</h3>
            <form @submit.prevent="submitForm" class="contact-form">
              <div class="form-group">
                <label for="name">Company / Contact Name *</label>
                <input type="text" id="name" v-model="form.name" required placeholder="Enter your full name" />
              </div>
              
              <div class="form-row">
                <div class="form-group">
                  <label for="email">Email Address *</label>
                  <input type="email" id="email" v-model="form.email" required placeholder="Enter your email" />
                </div>
                <div class="form-group">
                  <label for="phone">Phone Number</label>
                  <input type="tel" id="phone" v-model="form.phone" placeholder="Enter your phone" />
                </div>
              </div>
              
              <div class="form-group">
                <label for="message">Requirements / Message *</label>
                <textarea id="message" v-model="form.message" rows="5" required placeholder="Tell us about the trades and numbers you require..."></textarea>
              </div>
              
              <div v-if="submitMessage" class="form-message" :class="{ 'is-error': isError }">
                {{ submitMessage }}
              </div>
              
              <button type="submit" class="submit-btn" :disabled="isSubmitting">
                <Send size="18" /> {{ isSubmitting ? 'Sending...' : 'Send Message' }}
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
.page-header {
  background-color: var(--color-surface);
  padding: 60px 0 40px;
  border-bottom: 1px solid var(--color-border);
}

:deep(.page-title-header .title) {
  font-size: 48px;
  color: var(--color-primary-dark);
}

.contact-section {
  padding: 80px 0;
  background-color: var(--color-background);
}

.contact-container {
  display: flex;
  gap: 60px;
}

.contact-info {
  flex: 1;
}

.contact-info h3 {
  font-size: 28px;
  font-weight: 800;
  color: var(--color-primary-dark);
  margin-bottom: 20px;
}

.intro-p {
  color: var(--color-text-muted);
  font-size: 16px;
  line-height: 1.6;
  margin-bottom: 40px;
}

.info-cards {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.info-card {
  display: flex;
  align-items: flex-start;
  gap: 20px;
  background-color: var(--color-surface);
  padding: 24px;
  border-radius: var(--border-radius);
  border: 1px solid var(--color-border);
}

.icon-wrap {
  width: 50px;
  height: 50px;
  background-color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: var(--shadow-sm);
  flex-shrink: 0;
}

.info-icon {
  color: var(--color-accent);
}

.info-content h4 {
  font-size: 16px;
  color: var(--color-primary);
  margin-bottom: 8px;
}

.info-content p, .info-content a {
  color: var(--color-text-muted);
  font-size: 14px;
  line-height: 1.6;
}

.info-content a:hover {
  color: var(--color-accent);
}

/* Form Styles */
.contact-form-wrapper {
  flex: 1.2;
  background-color: white;
  padding: 40px;
  border-radius: var(--border-radius-lg);
  box-shadow: var(--shadow-lg);
  border: 1px solid var(--color-border);
}

.contact-form-wrapper h3 {
  font-size: 24px;
  font-weight: 800;
  margin-bottom: 30px;
  color: var(--color-text-main);
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.form-row {
  display: flex;
  gap: 20px;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 8px;
  flex: 1;
}

label {
  font-size: 13px;
  font-weight: 700;
  color: var(--color-primary);
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

input, textarea {
  padding: 14px 16px;
  border: 1px solid #d1d9e6;
  border-radius: var(--border-radius);
  font-family: var(--font-family);
  font-size: 15px;
  transition: border-color 0.3s;
  background-color: #fcfdfc;
}

input:focus, textarea:focus {
  outline: none;
  border-color: var(--color-accent);
  background-color: white;
}

.submit-btn {
  background-color: var(--color-primary);
  color: white;
  padding: 16px;
  border-radius: var(--border-radius);
  font-weight: 700;
  font-size: 16px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  border: none;
  cursor: pointer;
  transition: all 0.3s ease;
  margin-top: 10px;
}

.submit-btn:hover:not(:disabled) {
  background-color: var(--color-primary-dark);
  box-shadow: var(--shadow-md);
}

.submit-btn:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

.form-message {
  padding: 15px;
  border-radius: var(--border-radius);
  background-color: #d1e7dd;
  color: #0f5132;
  font-size: 14px;
  font-weight: 600;
}

.form-message.is-error {
  background-color: #f8d7da;
  color: #842029;
}

@media (max-width: 992px) {
  .contact-container {
    flex-direction: column;
  }
}

@media (max-width: 576px) {
  .form-row {
    flex-direction: column;
  }
}
</style>
