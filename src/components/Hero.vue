<template>
  <section class="hero" id="hero">
    <div class="hero-inner fade-up">
      <span class="hero-eyebrow">👋 Hello, I'm</span>
      <h1 class="hero-name">Daimler<br /><em>Fernandez</em></h1>
      <div class="hero-roles">
        <span v-for="(role, i) in roles" :key="role" class="hero-role" :style="`animation-delay: ${0.2 + i * 0.1}s`">
          {{ role }}
        </span>
      </div>
      <p class="hero-tagline">
        Building mission-critical systems that improve<br />efficiency in healthcare and beyond.
      </p>
      <div class="hero-cta">
        <a href="#projects" class="btn-primary">View Projects</a>
        <a href="#contact" class="btn-ghost">Get in Touch</a>
      </div>
    </div>

    <!-- Decorative grid lines -->
    <div class="hero-grid"></div>

    <!-- Floating badge -->
    <div class="hero-badge">
      <span class="badge-dot"></span>
      Available for opportunities
    </div>
  </section>
</template>

<script setup>
const roles = ['IT Professional','Tech Support', 'Full-Stack Developer', 'System Administrator'];
</script>

<style scoped>
.hero {
  min-height: 92vh;
  display: flex;
  align-items: center;
  position: relative;
  padding: 120px 0 60px;
  overflow: hidden;
}

.hero-inner {
  position: relative;
  z-index: 2;
}

.hero-eyebrow {
  font-family: var(--font-mono);
  font-size: 14px;
  color: var(--text-muted);
  letter-spacing: 1px;
  display: block;
  margin-bottom: 20px;
}

.hero-name {
  font-size: clamp(52px, 9vw, 96px);
  line-height: 1.05;
  margin-bottom: 28px;
  letter-spacing: -2px;
}

.hero-name em {
  font-style: italic;
  background: linear-gradient(135deg, var(--accent), var(--accent-2));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero-roles {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 32px;
}

.hero-role {
  font-family: var(--font-mono);
  font-size: 12px;
  letter-spacing: 1px;
  color: var(--accent);
  border: 1px solid rgba(56, 189, 248, 0.3);
  padding: 6px 14px;
  border-radius: 100px;
  background: rgba(56, 189, 248, 0.05);
  animation: fadeUp 0.6s ease both;
}

.hero-tagline {
  font-size: 18px;
  color: var(--text-secondary);
  max-width: 460px;
  line-height: 1.7;
  margin-bottom: 44px;
}

.hero-cta {
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
}

.btn-primary {
  display: inline-block;
  padding: 14px 32px;
  background: var(--accent);
  color: #080e1a;
  font-family: var(--font-body);
  font-weight: 600;
  font-size: 15px;
  border-radius: 10px;
  text-decoration: none;
  transition: opacity 0.2s, transform 0.2s;
}

.btn-primary:hover { opacity: 0.85; transform: translateY(-2px); }

.btn-ghost {
  display: inline-block;
  padding: 14px 32px;
  border: 1px solid var(--border);
  color: var(--text-secondary);
  font-size: 15px;
  border-radius: 10px;
  text-decoration: none;
  transition: border-color 0.2s, color 0.2s, transform 0.2s;
}

.btn-ghost:hover {
  border-color: var(--accent);
  color: var(--accent);
  transform: translateY(-2px);
}

/* Grid decoration */
.hero-grid {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(56, 189, 248, 0.04) 1px, transparent 1px),
    linear-gradient(90deg, rgba(56, 189, 248, 0.04) 1px, transparent 1px);
  background-size: 60px 60px;
  mask-image: radial-gradient(ellipse 80% 80% at 80% 50%, black 30%, transparent 100%);
  z-index: 1;
}

/* Availability badge */
.hero-badge {
  position: absolute;
  bottom: 60px;
  right: 0;
  display: flex;
  align-items: center;
  gap: 8px;
  font-family: var(--font-mono);
  font-size: 11px;
  color: var(--text-muted);
  letter-spacing: 1px;
  z-index: 2;
}

.badge-dot {
  width: 8px;
  height: 8px;
  background: #4ade80;
  border-radius: 50%;
  box-shadow: 0 0 0 0 rgba(74, 222, 128, 0.4);
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0% { box-shadow: 0 0 0 0 rgba(74, 222, 128, 0.4); }
  70% { box-shadow: 0 0 0 8px rgba(74, 222, 128, 0); }
  100% { box-shadow: 0 0 0 0 rgba(74, 222, 128, 0); }
}
</style>
