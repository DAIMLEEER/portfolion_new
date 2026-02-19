<template>
  <section id="contact">
    <span class="section-label">06 — Contact</span>
    <h2 class="section-title">Get in Touch</h2>
    <div class="section-divider"></div>

    <div class="contact-wrapper card">
      <div class="contact-left">
        <p class="contact-intro">
          Have a project in mind, or just want to connect? Feel free to reach out — I'm always
          open to interesting conversations and new opportunities.
        </p>

        <div class="contact-links">
          <a v-for="item in contactItems" :key="item.label"
             :href="item.href" class="contact-item" target="_blank">
            <span class="contact-icon">{{ item.icon }}</span>
            <div>
              <span class="contact-label">{{ item.label }}</span>
              <span class="contact-value">{{ item.value }}</span>
            </div>
          </a>
        </div>
      </div>

      <div class="contact-cta">
        <p class="cta-text">Open to roles in</p>
        <div class="cta-tags">
          <span v-for="role in openRoles" :key="role" class="cta-tag">{{ role }}</span>
        </div>
        <a href="mailto:daimler00000@gmail.com" class="btn-primary email-btn">
          Say Hello →
        </a>
      </div>
    </div>

    <footer class="footer">
      <span>Built with Vue.js · {{ new Date().getFullYear() }}</span>
      <span>Daimler Fernandez</span>
    </footer>
  </section>
</template>

<script setup>
const contactItems = [
  { icon: '✉️', label: 'Email', value: 'daimler00000@gmail.com', href: 'mailto:daimler00000@gmail.com' },
  { icon: '💼', label: 'LinkedIn', value: 'Daimler Fernandez', href: 'https://www.linkedin.com/in/daimler-fernandez-717bb3381' },
  { icon: '🐙', label: 'GitHub', value: 'Daimler Fernandez', href: 'https://github.com/DAIMLEEER' },
];

const openRoles = ['IT Systems Admin', 'Full-Stack Dev', 'Healthcare IT', 'DevOps','Tech Support'];
</script>

<style scoped>
.contact-wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  padding: 48px;
}

.contact-intro {
  font-size: 15.5px;
  line-height: 1.75;
  margin-bottom: 36px;
}

.contact-links {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.contact-item {
  display: flex;
  align-items: center;
  gap: 16px;
  text-decoration: none;
  padding: 14px 16px;
  border-radius: 10px;
  border: 1px solid var(--border);
  background: var(--surface-2);
  transition: border-color 0.2s, transform 0.2s;
}

.contact-item:hover {
  border-color: var(--accent);
  transform: translateX(4px);
}

.contact-icon { font-size: 20px; }

.contact-label {
  display: block;
  font-family: var(--font-mono);
  font-size: 10px;
  letter-spacing: 1px;
  text-transform: uppercase;
  color: var(--text-muted);
  margin-bottom: 2px;
}

.contact-value {
  display: block;
  font-size: 14px;
  color: var(--text-primary);
}

.cta-text {
  font-family: var(--font-mono);
  font-size: 11px;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: var(--text-muted);
  margin-bottom: 14px;
}

.cta-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 36px;
}

.cta-tag {
  font-family: var(--font-mono);
  font-size: 11px;
  color: var(--accent-2);
  background: rgba(129, 140, 248, 0.08);
  border: 1px solid rgba(129, 140, 248, 0.2);
  padding: 5px 12px;
  border-radius: 6px;
}

.email-btn {
  display: inline-block;
  padding: 16px 36px;
  background: var(--accent);
  color: #080e1a;
  font-family: var(--font-body);
  font-weight: 600;
  font-size: 15px;
  border-radius: 10px;
  text-decoration: none;
  transition: opacity 0.2s, transform 0.2s;
}

.email-btn:hover { opacity: 0.85; transform: translateY(-2px); }

.footer {
  display: flex;
  justify-content: space-between;
  margin-top: 80px;
  padding-top: 32px;
  border-top: 1px solid var(--border);
  font-family: var(--font-mono);
  font-size: 11px;
  letter-spacing: 1px;
  color: var(--text-muted);
}

@media (max-width: 640px) {
  .contact-wrapper { grid-template-columns: 1fr; gap: 40px; padding: 28px; }
  .footer { flex-direction: column; gap: 8px; }
}
</style>
