<script setup>
import SectionHeader from '../ui/SectionHeader.vue'
import { Users, UserPlus, FileCheck, ClipboardList, Briefcase, Bus } from 'lucide-vue-next'

const services = [
  {
    icon: Users,
    title: 'Manpower Supply',
    desc: 'Short & long term skilled and semi-skilled staff.'
  },
  {
    icon: UserPlus,
    title: 'Recruitment & Onboarding',
    desc: 'Screening, selection and fast deployment.'
  },
  {
    icon: FileCheck,
    title: 'Visa, Payroll & Compliance',
    desc: 'Visa processing, WPS payroll, insurance & MOHRE compliance.'
  },
  {
    icon: ClipboardList,
    title: 'Workforce Management',
    desc: 'Attendance, transport & accommodation coordination.'
  },
  {
    icon: Briefcase,
    title: 'HR Consultancy',
    desc: 'HR solutions that improve productivity and efficiency.'
  },
  {
    icon: Bus,
    title: 'Accommodation & Transportation',
    desc: 'Safe living and transport solutions for your workforce.'
  }
]
</script>

<template>
  <section class="services-section">
    <div class="container">
      <SectionHeader subtitle="OUR CORE SERVICES" title="" :centered="true" />
      
      <div class="services-grid">
        <div v-for="(service, index) in services" :key="index" class="service-card">
          <div class="service-icon-wrap">
            <component :is="service.icon" size="32" class="service-icon" />
          </div>
          <h3 class="service-title">{{ service.title }}</h3>
          <p class="service-desc">{{ service.desc }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.services-section {
  padding: 80px 0;
  background-color: var(--color-surface);
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 30px;
  margin-top: 50px;
}

.service-card {
  background-color: white;
  border-radius: var(--border-radius);
  padding: 40px 30px;
  text-align: center;
  box-shadow: var(--shadow-sm);
  transition: all 0.3s ease;
  border-bottom: 3px solid transparent;
}

.service-card:hover {
  transform: translateY(-5px);
  box-shadow: var(--shadow-lg);
  border-bottom-color: var(--color-accent);
}

.service-icon-wrap {
  width: 80px;
  height: 80px;
  margin: 0 auto 20px;
  background-color: var(--color-surface);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background-color 0.3s ease;
}

.service-card:hover .service-icon-wrap {
  background-color: var(--color-primary);
}

.service-icon {
  color: var(--color-primary);
  transition: color 0.3s ease;
}

.service-card:hover .service-icon {
  color: white;
}

.service-title {
  font-size: 18px;
  font-weight: 700;
  color: var(--color-text-main);
  margin-bottom: 15px;
}

.service-desc {
  font-size: 14px;
  color: var(--color-text-muted);
  line-height: 1.5;
}
</style>
