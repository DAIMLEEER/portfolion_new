<template>
  <section id="about">
    <span class="section-label">01 — About</span>
    <h2 class="section-title">Who I Am</h2>
    <div class="section-divider"></div>

    <div class="about-grid">
      <div class="about-text">
        <p class="about-lead">
          IT Professional with <strong>5+ years of experience</strong> in healthcare IT,
          full-stack development, and system administration.
        </p>
        <p>
          Specialized in Laravel, MySQL, automation, and infrastructure support. I thrive at the
          intersection of software engineering and operations — building reliable systems that
          healthcare teams can depend on every day.
        </p>
        <p>
          Currently serving as IT Support & Systems Administrator at Gensan Medical Center,
          where I architect and maintain mission-critical platforms used by 100+ staff.
        </p>
      </div>

      <div class="about-stats">
        <div class="stat-card" v-for="stat in stats" :key="stat.label">
          <span class="stat-number">{{ stat.value }}</span>
          <span class="stat-label">{{ stat.label }}</span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const stats = [
  { value: '5+', label: 'Years Experience' },
  { value: '100+', label: 'Staff Supported' },
  { value: '99.5%', label: 'System Uptime' },
  { value: '90min', label: 'Avg. Resolution Time' },
];
</script>

<style scoped>
.about-grid {
  display: grid;
  grid-template-columns: 1fr 340px;
  gap: 60px;
  align-items: start;
}

.about-lead {
  font-size: 18px;
  color: var(--text-primary);
  margin-bottom: 20px;
}

.about-lead strong {
  color: var(--accent);
  font-weight: 600;
}

.about-text p + p {
  margin-top: 16px;
}

.about-stats {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

.stat-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 14px;
  padding: 24px 20px;
  display: flex;
  flex-direction: column;
  gap: 6px;
  transition: border-color 0.3s;
}

.stat-card:hover { border-color: rgba(56, 189, 248, 0.35); }

.stat-number {
  font-family: var(--font-display);
  font-size: 32px;
  color: var(--accent);
  line-height: 1;
}

.stat-label {
  font-family: var(--font-mono);
  font-size: 11px;
  letter-spacing: 1px;
  color: var(--text-muted);
  text-transform: uppercase;
}

@media (max-width: 768px) {
  .about-grid { grid-template-columns: 1fr; }
}
</style>
