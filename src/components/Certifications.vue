<template>
  <section id="certifications">
    <span class="section-label">05 — Certifications</span>
    <h2 class="section-title">Credentials</h2>
    <div class="section-divider"></div>

    <div class="cert-grid">
      <div
        class="cert-card card"
        v-for="cert in certifications"
        :key="cert.credentialId + cert.name"
      >
        <div class="cert-icon">{{ cert.icon }}</div>

        <div class="cert-body">
          <h3 class="cert-name">{{ cert.name }}</h3>
          <p class="cert-issuer">{{ cert.issuer }}</p>

          <div class="cert-meta">
            <span class="cert-date">{{ cert.issued }}</span>
            <span class="cert-id">ID: {{ cert.credentialId }}</span>
          </div>

          <a
            v-if="cert.file"
            :href="cert.file"
            target="_blank"
            rel="noopener noreferrer"
            class="cert-link"
          >
            View Certificate &#8599;
          </a>
        </div>
      </div>
    </div>

    <p v-if="certifications.length === 0" class="empty-state">
      Certifications coming soon — stay tuned.
    </p>
  </section>
</template>

<script setup>
import googleAdsCert from '@/assets/certificates/Google ads.pdf'
import googleBitsCert from '@/assets/certificates/Google Bits by Byte.pdf'
import googleITCert from '@/assets/certificates/Google IT Security.pdf'
import googleOSCert from '@/assets/certificates/Google OS.pdf'
import googleSysAdminCert from '@/assets/certificates/Google System Admin.pdf'
import microsoft365Cert from '@/assets/certificates/Microsoft 365.pdf'

const certifications = [
  {
    icon: '🎯',
    name: 'Google Ads for Beginners',
    issuer: 'Coursera',
    issued: 'Jan 2026',
    credentialId: 'Z2JJ6ZIAJPYO',
    file: googleAdsCert,
  },
  {
    icon: '🎯',
    name: 'The Bits and Bytes of Computer Networking',
    issuer: 'Google',
    credentialId: '6MJ6V9JZ6XEB',
    file: googleBitsCert,
  },
  {
    icon: '🎯',
    name: 'Operating Systems and You: Becoming a Power User',
    issuer: 'Google',
    credentialId:  'Z7VVG24L3MPQ',
    file: googleOSCert,
  },
  {
    icon: '🎯',
    name: ' System Administration and IT Infrastructure Services',
    issuer: 'Google',
    credentialId: 'SQFB7IL4DRQX',
    file: googleSysAdminCert,
  },
  {
    icon: '🎯',
    name: 'IT Security: Defense against the digital dark arts ',
    issuer: 'Google',
    credentialId: 'JWOUZAXBTOFY',
    file: googleITCert,
  },
  {
    icon: '🎯',
    name: 'The Microsoft 365 Ecosystem',
    issuer: 'Microsoft',
    credentialId: 'N2PD4KUZCL9R',
    file: microsoft365Cert,
  },
]
</script>

<style scoped>
.cert-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 16px;
}

.cert-card {
  display: flex;
  align-items: flex-start;
  gap: 20px;
  padding: 24px;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.cert-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.12);
}

.cert-icon {
  font-size: 32px;
  flex-shrink: 0;
}

.cert-body {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.cert-name {
  font-size: 15px;
  color: var(--text-primary);
  margin: 0;
}

.cert-issuer {
  font-size: 13px;
  color: var(--text-muted);
  margin: 0;
}

.cert-meta {
  display: flex;
  flex-direction: column;
  gap: 2px;
  margin-top: 4px;
}

.cert-date {
  font-family: var(--font-mono);
  font-size: 11px;
  color: var(--accent);
  letter-spacing: 1px;
}

.cert-id {
  font-family: var(--font-mono);
  font-size: 10px;
  color: var(--text-muted);
  letter-spacing: 0.5px;
}

.cert-link {
  display: inline-block;
  margin-top: 10px;
  font-size: 12px;
  font-family: var(--font-mono);
  color: var(--accent);
  text-decoration: none;
  letter-spacing: 0.5px;
  transition: opacity 0.2s;
}

.cert-link:hover {
  opacity: 0.7;
  text-decoration: underline;
}

.empty-state {
  font-family: var(--font-mono);
  font-size: 13px;
  color: var(--text-muted);
  text-align: center;
  padding: 48px;
  border: 1px dashed var(--border);
  border-radius: 16px;
  letter-spacing: 1px;
}
</style>