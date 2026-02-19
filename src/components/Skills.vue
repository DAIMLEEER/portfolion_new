<template>
  <section id="skills">
    <span class="section-label">02 — Skills</span>
    <h2 class="section-title">Technical Stack</h2>
    <div class="section-divider"></div>

    <div class="skill-groups">
      <div class="skill-group card" v-for="group in skillGroups" :key="group.category">
        <div class="group-header">
          <span class="group-icon">{{ group.icon }}</span>
          <span class="group-category">{{ group.category }}</span>
        </div>
        <div class="skill-tags">
          <span class="skill-tag" v-for="skill in group.skills" :key="skill">
            {{ skill }}
          </span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const skillGroups = [
  {
    icon: '⚙️',
    category: 'Backend & Frameworks',
    skills: ['Laravel', 'PHP', 'C# .NET', 'REST APIs'],
  },
  {
    icon: '🗄️',
    category: 'Databases',
    skills: ['MySQL', 'MSSQL', 'Query Optimization', 'Database Design'],
  },
  {
    icon: '🖥️',
    category: 'Frontend',
    skills: ['Vue.js', 'JavaScript', 'HTML/CSS', 'Responsive Design'],
  },
  {
    icon: '🚀',
    category: 'Infrastructure & DevOps',
    skills: ['Docker', 'Network Administration', 'Automation (n8n)', 'Linux'],
  },
];
</script>

<style scoped>
.skill-groups {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
}

.skill-group {
  padding: 28px;
}

.group-header {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 20px;
}

.group-icon {
  font-size: 20px;
}

.group-category {
  font-family: var(--font-mono);
  font-size: 12px;
  letter-spacing: 1px;
  text-transform: uppercase;
  color: var(--text-muted);
}

.skill-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.skill-tag {
  font-size: 13px;
  font-weight: 500;
  color: var(--text-primary);
  background: var(--surface-2);
  border: 1px solid rgba(56, 189, 248, 0.15);
  padding: 6px 14px;
  border-radius: 8px;
  transition: border-color 0.2s, color 0.2s;
}

.skill-tag:hover {
  border-color: var(--accent);
  color: var(--accent);
}

@media (max-width: 640px) {
  .skill-groups { grid-template-columns: 1fr; }
}
</style>
