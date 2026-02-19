<template>
  <section id="projects">
    <span class="section-label">03 — Projects</span>
    <h2 class="section-title">Selected Work</h2>
    <div class="section-divider"></div>

    <div class="projects-list">
      <div class="project-card card" v-for="(project, i) in projects" :key="project.title">
        <div class="project-header">
          <span class="project-number">0{{ i + 1 }}</span>
          <div class="project-links">
            <a v-if="project.link" :href="project.link" class="project-link" target="_blank">↗</a>
          </div>
        </div>
        <h3 class="project-title">{{ project.title }}</h3>
        <p class="project-desc">{{ project.description }}</p>
        <div class="project-tech">
          <span class="tech-tag" v-for="tech in project.tech" :key="tech">{{ tech }}</span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const projects = [
  {
    title: 'Biometric Payroll System',
    description: 'Workforce management platform handling 200+ employees with automated payroll computation, attendance tracking, leave management, and comprehensive reporting dashboards.',
    tech: ['C#', '.NET', 'MySQL', 'WinForms'],
    link: null,
  },
  {
    title: 'WiFi Voucher Management System',
    description: 'Automated voucher generation and real-time monitoring system for hospital guest Wi-Fi. Includes an admin panel with usage analytics, expiry control, and batch generation.',
    tech: ['PHP', 'MySQL', 'JavaScript', 'Bootstrap'],
    link: null,
  },
  {
    title: 'Hospital Information System Integration',
    description: 'Integrated multiple hospital modules including patient records, billing, and pharmacy into a unified system, reducing data entry errors and improving staff workflow efficiency.',
    tech: ['Laravel', 'Vue.js', 'MSSQL', 'REST API'],
    link: null,
  },
];
</script>

<style scoped>
.projects-list {
  display: grid;
  gap: 20px;
}

.project-card {
  padding: 36px;
  position: relative;
  overflow: hidden;
}

.project-card::before {
  content: '';
  position: absolute;
  top: 0; left: 0;
  width: 3px;
  height: 100%;
  background: linear-gradient(180deg, var(--accent), var(--accent-2));
  border-radius: 2px 0 0 2px;
  opacity: 0;
  transition: opacity 0.3s;
}

.project-card:hover::before { opacity: 1; }

.project-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 16px;
}

.project-number {
  font-family: var(--font-mono);
  font-size: 11px;
  letter-spacing: 2px;
  color: var(--accent);
  opacity: 0.7;
}

.project-link {
  font-size: 18px;
  color: var(--text-muted);
  text-decoration: none;
  transition: color 0.2s;
}

.project-link:hover { color: var(--accent); }

.project-title {
  font-size: 22px;
  margin-bottom: 14px;
  color: var(--text-primary);
}

.project-desc {
  font-size: 15px;
  line-height: 1.75;
  margin-bottom: 24px;
}

.project-tech {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.tech-tag {
  font-family: var(--font-mono);
  font-size: 11px;
  letter-spacing: 0.5px;
  color: var(--accent);
  background: rgba(56, 189, 248, 0.08);
  border: 1px solid rgba(56, 189, 248, 0.2);
  padding: 4px 12px;
  border-radius: 6px;
}
</style>
