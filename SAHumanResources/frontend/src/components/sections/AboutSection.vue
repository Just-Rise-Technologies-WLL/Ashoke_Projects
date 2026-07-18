<script setup>
import { ArrowRight, ShieldCheck } from 'lucide-vue-next'
import Button from '../ui/Button.vue'
</script>

<template>
  <section class="about-section">
    <div class="container about-container">
      
      <div class="about-image-wrapper">
        <img src="https://images.unsplash.com/photo-1504307651254-35680f356f54?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Construction Work" class="about-image" />
        <div class="badge">
          <ShieldCheck size="32" class="badge-icon" />
          <div class="badge-text">
            <strong>MOHRE</strong>
            <span>COMPLIANT</span>
          </div>
        </div>
      </div>
      
      <div class="about-content">
        <div class="section-tag">ABOUT US</div>
        <h2 class="section-title">Building Projects<br/>With The Right People</h2>
        
        <div class="section-text">
          <p>
            <b>SHAJAD AHMAD HR CONSULTANCIES L.L.C.</b> is a Sharjah-based manpower supply and HR consultancy specializing in skilled and semi-skilled labour for the construction, fit-out, and building maintenance industries across the UAE.
          </p>
          <p>
            We bridge the gap between site-level operational demands and a vetted, ready-to-deploy workforce, offering scalable, fully compliant, and cost-effective staffing solutions.
          </p>
        </div>
        
        <Button to="/about" variant="primary">
          READ MORE ABOUT US <ArrowRight size="16" />
        </Button>
      </div>

    </div>
  </section>
</template>

<style scoped>
.about-section {
  padding: 100px 0;
  background-color: var(--color-background);
}

.about-container {
  display: flex;
  align-items: center;
  gap: 60px;
}

.about-image-wrapper {
  flex: 1;
  position: relative;
  border-radius: 20px;
  overflow: visible; /* to allow badge to overflow */
}

.about-image {
  width: 100%;
  height: 500px;
  object-fit: cover;
  border-radius: 20px;
  box-shadow: var(--shadow-lg);
}

.badge {
  position: absolute;
  bottom: -30px;
  left: 40px;
  background-color: white;
  padding: 20px 30px;
  border-radius: 12px;
  display: flex;
  align-items: center;
  gap: 15px;
  box-shadow: var(--shadow-lg);
  border: 1px solid var(--color-border);
}

.badge-icon {
  color: var(--color-accent);
}

.badge-text {
  display: flex;
  flex-direction: column;
}

.badge-text strong {
  font-size: 18px;
  color: var(--color-primary-dark);
  line-height: 1;
}

.badge-text span {
  font-size: 12px;
  color: var(--color-text-muted);
  font-weight: 600;
  letter-spacing: 1px;
}

.about-content {
  flex: 1;
}

.section-tag {
  color: var(--color-accent);
  font-weight: 700;
  font-size: 14px;
  letter-spacing: 1px;
  margin-bottom: 12px;
}

.section-title {
  font-size: 42px;
  font-weight: 800;
  color: var(--color-primary-dark);
  line-height: 1.2;
  margin-bottom: 24px;
}

.section-text {
  color: var(--color-text-muted);
  font-size: 16px;
  margin-bottom: 32px;
  display: flex;
  flex-direction: column;
  gap: 16px;
}

@media (max-width: 992px) {
  .about-container {
    flex-direction: column;
  }
  .about-image-wrapper {
    width: 100%;
    margin-bottom: 40px;
  }
  .badge {
    bottom: -20px;
    left: 20px;
  }
}

@media (max-width: 768px) {
  .section-title {
    font-size: 32px;
  }
}
</style>
