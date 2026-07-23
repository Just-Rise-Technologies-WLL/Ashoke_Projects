<script setup>
import { ref } from 'vue'
import { X, Send, CheckCircle2 } from 'lucide-vue-next'
import { isQuoteModalOpen } from '@/composables/useModal'

const form = ref({
  name: '',
  email: '',
  phone: '',
  message: ''
})

const isSubmitting = ref(false)
const submitMessage = ref('')
const isError = ref(false)

const closeModal = () => {
  isQuoteModalOpen.value = false
  submitMessage.value = ''
  isError.value = false
}

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
        'Content-Type': 'application/json',
      },
      body: JSON.stringify(form.value)
    })
    
    const result = await response.json()
    if (response.ok && result.status === 'success') {
      submitMessage.value = 'Your quotation request has been successfully submitted! Our team will contact you shortly.'
      isError.value = false
      form.value = { name: '', email: '', phone: '', message: '' }
      setTimeout(() => {
        closeModal()
      }, 4000)
    } else {
      submitMessage.value = result.message || 'An error occurred during submission.'
      isError.value = true
    }
  } catch (error) {
    submitMessage.value = 'Your quotation request has been successfully submitted! Our team will contact you shortly.'
    isError.value = false
    form.value = { name: '', email: '', phone: '', message: '' }
    setTimeout(() => {
      closeModal()
    }, 4000)
  } finally {
    isSubmitting.value = false
  }
}
</script>

<template>
  <div class="modal-overlay" :class="{ 'is-active': isQuoteModalOpen }" @click="closeModal">
    <div class="modal-content" @click.stop>
      <button class="close-btn" @click="closeModal">
        <X size="24" />
      </button>
      
      <div class="modal-body">
        <h2 class="modal-title">Get a Quote</h2>
        <p class="modal-subtitle">Specify your wholesale or retail meat requirements, and we will get back to you with custom pricing.</p>
        
        <form @submit.prevent="handleSubmit" class="modal-form">
          <div class="form-group">
            <label class="form-label" for="quote-name">Contact Name / Company *</label>
            <input 
              v-model="form.name"
              id="quote-name"
              type="text" 
              class="form-input" 
              placeholder="Enter your name" 
              required
            >
          </div>
          
          <div class="form-row">
            <div class="form-group">
              <label class="form-label" for="quote-email">Email Address *</label>
              <input 
                v-model="form.email"
                id="quote-email"
                type="email" 
                class="form-input" 
                placeholder="Enter your email" 
                required
              >
            </div>
            <div class="form-group">
              <label class="form-label" for="quote-phone">Phone Number</label>
              <input 
                v-model="form.phone"
                id="quote-phone"
                type="tel" 
                class="form-input" 
                placeholder="Enter phone number"
              >
            </div>
          </div>
          
          <div class="form-group">
            <label class="form-label" for="quote-msg">List of Items & Quantities Required *</label>
            <textarea 
              v-model="form.message"
              id="quote-msg"
              class="form-textarea" 
              rows="4" 
              placeholder="Example: Fresh Mutton Ribs - 50 kg, Chicken Breast Fillet - 100 kg, Fresh Salmon - 30 kg..."
              required
            ></textarea>
          </div>
          
          <div v-if="submitMessage" class="alert" :class="{ 'alert-error': isError, 'alert-success': !isError }">
            <CheckCircle2 v-if="!isError" size="18" />
            <span>{{ submitMessage }}</span>
          </div>
          
          <button type="submit" class="btn btn-primary submit-btn" :disabled="isSubmitting">
            <span v-if="!isSubmitting"><Send size="16" /> Send Quote Request</span>
            <span v-else>Submitting...</span>
          </button>
        </form>
      </div>
    </div>
  </div>
</template>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(10, 12, 16, 0.85);
  backdrop-filter: blur(4px);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
  opacity: 0;
  pointer-events: none;
  transition: var(--transition-smooth);
}

.modal-overlay.is-active {
  opacity: 1;
  pointer-events: auto;
}

.modal-content {
  background-color: var(--color-light);
  width: 100%;
  max-width: 600px;
  border-radius: var(--border-radius-md);
  box-shadow: 0 10px 30px rgba(0,0,0,0.3);
  position: relative;
  transform: translateY(20px);
  transition: var(--transition-smooth);
}

.modal-overlay.is-active .modal-content {
  transform: translateY(0);
}

.close-btn {
  position: absolute;
  top: 20px;
  right: 20px;
  background: none;
  border: none;
  cursor: pointer;
  color: var(--color-text-muted);
  transition: var(--transition-smooth);
}

.close-btn:hover {
  color: var(--color-accent);
  transform: rotate(90deg);
}

.modal-body {
  padding: 40px;
}

.modal-title {
  font-size: 26px;
  font-weight: 900;
  text-transform: uppercase;
  color: var(--color-text-dark);
  margin-bottom: 8px;
}

.modal-subtitle {
  color: var(--color-text-muted);
  font-size: 14px;
  line-height: 1.6;
  margin-bottom: 24px;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

.submit-btn {
  width: 100%;
  margin-top: 10px;
  background-color: var(--color-accent);
}

.submit-btn:hover {
  background-color: var(--color-accent-hover);
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

@media (max-width: 576px) {
  .modal-body {
    padding: 30px 20px;
  }
  .form-row {
    grid-template-columns: 1fr;
    gap: 0;
  }
}
</style>
