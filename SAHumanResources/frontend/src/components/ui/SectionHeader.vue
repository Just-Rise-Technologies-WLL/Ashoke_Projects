<script setup>
defineProps({
  subtitle: {
    type: String,
    required: true
  },
  title: {
    type: String,
    required: true
  },
  centered: {
    type: Boolean,
    default: true
  }
})
</script>

<template>
  <div class="section-header" :class="{ 'is-centered': centered }">
    <div class="subtitle-wrap">
      <span class="line"></span>
      <span class="subtitle">{{ subtitle }}</span>
      <span class="line"></span>
    </div>
    <h2 class="title">{{ title }}</h2>
  </div>
</template>

<style scoped>
.section-header {
  margin-bottom: 40px;
}

.is-centered {
  text-align: center;
}

.is-centered .subtitle-wrap {
  justify-content: center;
}

.subtitle-wrap {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 12px;
}

.line {
  height: 1px;
  width: 40px;
  background-color: var(--color-accent);
}

.subtitle {
  color: var(--color-primary);
  font-weight: 700;
  font-size: 14px;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.title {
  font-size: 32px;
  font-weight: 800;
  color: var(--color-text-main);
  text-transform: capitalize;
}

@media (max-width: 768px) {
  .title {
    font-size: 26px;
  }
}
</style>
