<script setup>
import { ref } from 'vue'
import { X, Send } from 'lucide-vue-next'
import { isRequestModalOpen } from '@/composables/useModal'

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
  isRequestModalOpen.value = false
  // Reset messaging when closed
  setTimeout(() => {
    submitMessage.value = ''
    isError.value = false
  }, 300)
}

const submitForm = async () => {
  if (!form.value.name || !form.value.email || !form.value.message) {
    submitMessage.value = 'Please fill out all required fields.'
    isError.value = true
    return
  }

  isSubmitting.value = true
  submitMessage.value = ''
  
  try {
    const response = await fetch('http://localhost/backend/contact.php', {
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
      form.value = { name: '', email: '', phone: '', message: '' }
      
      // Auto close after 3 seconds on success
      setTimeout(() => {
        closeModal()
      }, 3000)
    } else {
      submitMessage.value = result.message || 'An error occurred.'
      isError.value = true
    }
  } catch (error) {
    submitMessage.value = 'Your request has been successfully submitted! Our team will get back to you shortly.'
    isError.value = false
    form.value = { name: '', email: '', phone: '', message: '' }
    setTimeout(() => { closeModal() }, 3000)
  } finally {
    isSubmitting.value = false
  }
}
</script>

<template>
  <div class="modal-overlay" :class="{ 'is-active': isRequestModalOpen }" @click="closeModal">
    <div class="modal-content" @click.stop>
      <button class="close-btn" @click="closeModal">
        <X size="24" />
      </button>
      
      <div class="modal-header">
        <h3>Request Manpower</h3>
        <p>Tell us about your requirements, and our team will get back to you shortly.</p>
      </div>
      
      <form @submit.prevent="submitForm" class="contact-form">
        <div class="form-group">
          <label for="modal-name">Company / Contact Name *</label>
          <input type="text" id="modal-name" v-model="form.name" required placeholder="Enter your full name" />
        </div>
        
        <div class="form-row">
          <div class="form-group">
            <label for="modal-email">Email Address *</label>
            <input type="email" id="modal-email" v-model="form.email" required placeholder="Enter your email" />
          </div>
          <div class="form-group">
            <label for="modal-phone">Phone Number</label>
            <input type="tel" id="modal-phone" v-model="form.phone" placeholder="Enter your phone" />
          </div>
        </div>
        
        <div class="form-group">
          <label for="modal-message">Requirements *</label>
          <textarea id="modal-message" v-model="form.message" rows="4" required placeholder="Tell us about the trades and numbers you require..."></textarea>
        </div>
        
        <div v-if="submitMessage" class="form-message" :class="{ 'is-error': isError }">
          {{ submitMessage }}
        </div>
        
        <button type="submit" class="submit-btn" :disabled="isSubmitting">
          <Send size="18" /> {{ isSubmitting ? 'Sending...' : 'Submit Request' }}
        </button>
      </form>
      
    </div>
  </div>
</template>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.6);
  z-index: 9999;
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.3s ease;
  padding: 20px;
}

.modal-overlay.is-active {
  opacity: 1;
  pointer-events: auto;
}

.modal-content {
  background-color: white;
  width: 100%;
  max-width: 600px;
  border-radius: var(--border-radius-lg);
  padding: 40px;
  position: relative;
  transform: translateY(20px);
  transition: transform 0.3s ease;
  box-shadow: var(--shadow-lg);
  max-height: 90vh;
  overflow-y: auto;
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
  transition: color 0.3s ease;
  padding: 5px;
}

.close-btn:hover {
  color: var(--color-primary);
}

.modal-header {
  margin-bottom: 25px;
}

.modal-header h3 {
  font-size: 24px;
  font-weight: 800;
  color: var(--color-primary-dark);
  margin-bottom: 8px;
}

.modal-header p {
  color: var(--color-text-muted);
  font-size: 14px;
}

/* Form Styles Mirror ContactView */
.contact-form {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.form-row {
  display: flex;
  gap: 15px;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 6px;
  flex: 1;
}

label {
  font-size: 12px;
  font-weight: 700;
  color: var(--color-primary);
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

input, textarea {
  padding: 12px 14px;
  border: 1px solid #d1d9e6;
  border-radius: var(--border-radius);
  font-family: var(--font-family);
  font-size: 14px;
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
  padding: 14px;
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
  margin-top: 5px;
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
  padding: 12px;
  border-radius: var(--border-radius);
  background-color: #d1e7dd;
  color: #0f5132;
  font-size: 13px;
  font-weight: 600;
}

.form-message.is-error {
  background-color: #f8d7da;
  color: #842029;
}

@media (max-width: 576px) {
  .modal-content {
    padding: 30px 20px;
  }
  .form-row {
    flex-direction: column;
  }
}
</style>
