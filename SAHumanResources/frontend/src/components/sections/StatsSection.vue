<script setup>
import { Users, Clock, ShieldCheck, Award, Briefcase } from 'lucide-vue-next'
</script>

<template>
  <section class="stats-section">
    <div class="container stats-container">
      
      <div class="stat-item">
        <Users size="48" class="stat-icon" />
        <div class="stat-content">
          <div class="stat-num">500+</div>
          <div class="stat-label">Skilled Workforce<br/>Available</div>
        </div>
      </div>
      
      <div class="stat-item">
        <Clock size="48" class="stat-icon" />
        <div class="stat-content">
          <div class="stat-num">24/7</div>
          <div class="stat-label">Rapid Response &<br/>Mobilization</div>
        </div>
      </div>

      <div class="stat-item">
        <ShieldCheck size="48" class="stat-icon" />
        <div class="stat-content">
          <div class="stat-num">100%</div>
          <div class="stat-label">MOHRE Compliant<br/>Processes</div>
        </div>
      </div>

      <div class="stat-item">
        <Award size="48" class="stat-icon" />
        <div class="stat-content">
          <div class="stat-num">10+</div>
          <div class="stat-label">Years of Industry<br/>Experience</div>
        </div>
      </div>

      <div class="stat-item">
        <Briefcase size="48" class="stat-icon" />
        <div class="stat-content">
          <div class="stat-num">100+</div>
          <div class="stat-label">Projects Successfully<br/>Supported</div>
        </div>
      </div>

    </div>
  </section>
</template>

<style scoped>
.stats-section {
  background-color: var(--color-primary-dark);
  margin-top: -40px; /* Overlap hero slightly */
  position: relative;
  z-index: 10;
  border-radius: var(--border-radius-lg);
  max-width: 1320px;
  margin-left: auto;
  margin-right: auto;
  padding: 40px;
  box-shadow: var(--shadow-lg);
}

.stats-container {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 20px;
}

.stat-item {
  display: flex;
  align-items: center;
  gap: 16px;
  color: white;
  flex: 1;
  min-width: 200px;
}

.stat-icon {
  color: var(--color-accent);
  stroke-width: 1.5;
}

.stat-num {
  font-size: 32px;
  font-weight: 800;
  line-height: 1.2;
}

.stat-label {
  font-size: 13px;
  font-weight: 500;
  color: #eeeeee;
  line-height: 1.4;
}

@media (max-width: 1024px) {
  .stats-section {
    margin-left: 20px;
    margin-right: 20px;
  }
}

@media (max-width: 768px) {
  .stats-section {
    margin-top: 0;
    border-radius: 0;
    padding: 30px 20px;
  }
  .stats-container {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 24px 16px;
  }
  .stat-item {
    min-width: 0;
  }
  .stat-item:nth-child(5) {
    grid-column: span 2;
    justify-self: center;
    max-width: 260px;
    width: 100%;
  }
}

@media (max-width: 576px) {
  .stats-container {
    grid-template-columns: 1fr;
    gap: 20px;
  }
  .stat-item:nth-child(5) {
    grid-column: span 1;
    justify-self: stretch;
    max-width: none;
  }
}
</style>
