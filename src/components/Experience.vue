<template>
  <section id="experience">
    <span class="section-label">04 — Experience</span>
    <h2 class="section-title">Work History</h2>
    <div class="section-divider"></div>

    <div class="timeline">
      <div class="timeline-item" v-for="job in experience" :key="job.company">
        <div class="timeline-marker">
          <div class="marker-dot"></div>
          <div class="marker-line"></div>
        </div>

        <div class="timeline-content card">
          <div class="job-header">
            <div>
              <h3 class="job-title">{{ job.title }}</h3>
              <p class="job-company">{{ job.company }}</p>
            </div>
            <span class="job-period">{{ job.period }}</span>
          </div>
          <ul class="job-bullets">
            <li v-for="bullet in job.bullets" :key="bullet">{{ bullet }}</li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const experience = [
  {
    title: 'IT Support & Systems Administrator',
    company: 'Gensan Medical Center',
    period: '2023 – Present',
    bullets: [
      'Provided Tier 1–2 technical support for 100+ clinical and administrative staff',
      'Maintained 99.5% system uptime across all critical hospital platforms',
      'Managed and optimized MySQL and MSSQL database instances',
      'Reduced average ticket resolution time to under 90 minutes',
      'Deployed and managed Docker-based services for internal tooling',
    ],
  },
];
</script>

<style scoped>
.timeline {
  display: flex;
  flex-direction: column;
  gap: 0;
}

.timeline-item {
  display: grid;
  grid-template-columns: 48px 1fr;
  gap: 24px;
  position: relative;
}

.timeline-marker {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 28px;
}

.marker-dot {
  width: 12px;
  height: 12px;
  background: var(--accent);
  border-radius: 50%;
  box-shadow: 0 0 0 4px rgba(56, 189, 248, 0.15);
  flex-shrink: 0;
  z-index: 1;
}

.marker-line {
  width: 1px;
  flex: 1;
  background: var(--border);
  margin-top: 8px;
}

.timeline-content {
  margin-bottom: 24px;
}

.job-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 20px;
  gap: 16px;
}

.job-title {
  font-size: 20px;
  color: var(--text-primary);
  margin-bottom: 4px;
}

.job-company {
  font-family: var(--font-mono);
  font-size: 12px;
  color: var(--accent);
  letter-spacing: 1px;
}

.job-period {
  font-family: var(--font-mono);
  font-size: 11px;
  color: var(--text-muted);
  letter-spacing: 1px;
  white-space: nowrap;
  background: var(--surface-2);
  padding: 4px 10px;
  border-radius: 6px;
  border: 1px solid var(--border);
}

.job-bullets {
  list-style: none;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.job-bullets li {
  font-size: 14.5px;
  color: var(--text-secondary);
  padding-left: 20px;
  position: relative;
  line-height: 1.6;
}

.job-bullets li::before {
  content: '→';
  position: absolute;
  left: 0;
  color: var(--accent);
  font-size: 12px;
}
</style>
