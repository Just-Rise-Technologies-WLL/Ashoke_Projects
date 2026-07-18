<script setup>
import SectionHeader from '../ui/SectionHeader.vue'
import { ShieldCheck, Zap, Users, Maximize, ClipboardCheck, Tag, HeartHandshake, HandHeart } from 'lucide-vue-next'

const features = [
  {
    icon: ShieldCheck,
    title: 'Strict Legal Compliance',
    desc: '100% adherence to UAE labour laws & MOHRE regulations.'
  },
  {
    icon: Zap,
    title: 'Fast Deployment',
    desc: 'Quick mobilization to keep your projects on track.'
  },
  {
    icon: Users,
    title: 'Verified Skilled Workforce',
    desc: 'Pre-screened, experienced and reliable workers.'
  },
  {
    icon: Maximize,
    title: 'Flexible Staffing Solutions',
    desc: 'Short-term or long-term staffing as per your need.'
  },
  {
    icon: ClipboardCheck,
    title: 'Hassle-Free Management',
    desc: 'We manage everything from visa to accommodation.'
  },
  {
    icon: Tag,
    title: 'Competitive Pricing',
    desc: 'Cost-effective manpower solutions without compromise.'
  },
  {
    icon: HeartHandshake,
    title: 'Experienced HR Team',
    desc: 'Dedicated professionals supporting your success.'
  },
  {
    icon: HandHeart,
    title: 'Worker Welfare Focused',
    desc: 'Safe environment, proper facilities & support.'
  }
]
</script>

<template>
  <section class="why-section">
    <div class="container">
      <SectionHeader subtitle="WHY PARTNER WITH US" title="" :centered="true" />
      
      <div class="features-grid">
        <div v-for="(feat, index) in features" :key="index" class="feature-item">
          <div class="feat-icon-wrap">
            <component :is="feat.icon" size="24" class="feat-icon" />
          </div>
          <div class="feat-content">
            <h4 class="feat-title">{{ feat.title }}</h4>
            <p class="feat-desc">{{ feat.desc }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.why-section {
  padding: 80px 0;
  background-color: var(--color-surface);
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 30px;
  margin-top: 40px;
}

.feature-item {
  display: flex;
  gap: 20px;
  background-color: white;
  padding: 30px 25px;
  border-radius: var(--border-radius);
  box-shadow: var(--shadow-sm);
  transition: all 0.3s ease;
}

.feature-item:hover {
  transform: translateY(-5px);
  box-shadow: var(--shadow-md);
}

.feat-icon-wrap {
  flex-shrink: 0;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background-color: var(--color-surface);
  display: flex;
  align-items: center;
  justify-content: center;
}

.feat-icon {
  color: var(--color-primary);
}

.feat-content {
  display: flex;
  flex-direction: column;
}

.feat-title {
  font-size: 16px;
  font-weight: 700;
  color: var(--color-text-main);
  margin-bottom: 8px;
}

.feat-desc {
  font-size: 13px;
  color: var(--color-text-muted);
  line-height: 1.5;
}
</style>
