<template>
  <div class="app">
    <!-- Sticky Nav -->
    <nav class="nav" :class="{ 'nav--scrolled': scrolled }">
      <span class="nav__logo">DF</span>
      <div class="nav__links">
        <a v-for="link in navLinks" :key="link" :href="`#${link.toLowerCase()}`">{{ link }}</a>
      </div>
    </nav>

    <!-- Background decoration -->
    <div class="bg-grid" aria-hidden="true"></div>
    <div class="bg-orb bg-orb--1" aria-hidden="true"></div>
    <div class="bg-orb bg-orb--2" aria-hidden="true"></div>

    <main class="container">
      <Hero />
      <About />
      <Skills />
      <Projects />
      <Experience />
      <Certifications />
      <Contact />
    </main>

    <footer class="footer">
      <span>© 2025 Daimler Fernandez · Built with Vue.js</span>
    </footer>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import Hero from './components/Hero.vue';
import About from './components/About.vue';
import Skills from './components/Skills.vue';
import Projects from './components/Projects.vue';
import Experience from './components/Experience.vue';
import Certifications from './components/Certifications.vue';
import Contact from './components/Contact.vue';

const navLinks = ['About', 'Skills', 'Projects', 'Experience', 'Certifications', 'Contact'];
const scrolled = ref(false);

function onScroll() {
  scrolled.value = window.scrollY > 60;
}

onMounted(() => {
  window.addEventListener('scroll', onScroll);

  // Scroll-reveal observer
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add('revealed');
          observer.unobserve(entry.target);
        }
      });
    },
    { threshold: 0.1 }
  );

  document.querySelectorAll('section').forEach((el) => observer.observe(el));
});

onUnmounted(() => window.removeEventListener('scroll', onScroll));
</script>

<style>
/* ─── Fonts ──────────────────────────────────────────────────────────────── */
@import url('https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;1,9..40,300&display=swap');

/* ─── Variables ──────────────────────────────────────────────────────────── */
:root {
  --bg:            #080c14;
  --bg-card:       #0d1424;
  --bg-card-hover: #111c33;
  --border:        rgba(255, 255, 255, 0.07);
  --border-accent: rgba(56, 189, 248, 0.35);
  --text:          #e2e8f0;
  --text-muted:    #64748b;
  --text-faint:    #1e293b;
  --accent:        #38bdf8;
  --accent-glow:   rgba(56, 189, 248, 0.12);
  --accent-2:      #818cf8;
  --radius:        12px;
  --ease:          cubic-bezier(0.4, 0, 0.2, 1);
  --transition:    0.3s var(--ease);
}

/* ─── Reset ──────────────────────────────────────────────────────────────── */
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; }

body {
  background: var(--bg);
  color: var(--text);
  font-family: 'DM Sans', sans-serif;
  font-size: 16px;
  line-height: 1.75;
  overflow-x: hidden;
  -webkit-font-smoothing: antialiased;
}

/* ─── Background ─────────────────────────────────────────────────────────── */
.bg-grid {
  position: fixed;
  inset: 0;
  pointer-events: none;
  z-index: 0;
  background-image:
    linear-gradient(rgba(56, 189, 248, 0.025) 1px, transparent 1px),
    linear-gradient(90deg, rgba(56, 189, 248, 0.025) 1px, transparent 1px);
  background-size: 64px 64px;
}

.bg-orb {
  position: fixed;
  border-radius: 50%;
  filter: blur(130px);
  pointer-events: none;
  z-index: 0;
}

.bg-orb--1 {
  width: 700px; height: 700px;
  background: radial-gradient(circle, rgba(56, 189, 248, 0.08) 0%, transparent 70%);
  top: -250px; right: -200px;
  animation: drift-a 22s ease-in-out infinite alternate;
}

.bg-orb--2 {
  width: 550px; height: 550px;
  background: radial-gradient(circle, rgba(129, 140, 248, 0.07) 0%, transparent 70%);
  bottom: 5%; left: -180px;
  animation: drift-b 28s ease-in-out infinite alternate;
}

@keyframes drift-a { to { transform: translate(-70px, 100px); } }
@keyframes drift-b { to { transform: translate(90px, -70px); } }

/* ─── Navigation ─────────────────────────────────────────────────────────── */
.nav {
  position: fixed; top: 0; left: 0; right: 0;
  z-index: 100;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 22px 48px;
  transition: var(--transition);
}

.nav--scrolled {
  background: rgba(8, 12, 20, 0.88);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border-bottom: 1px solid var(--border);
  padding: 14px 48px;
}

.nav__logo {
  font-family: 'Syne', sans-serif;
  font-weight: 800;
  font-size: 18px;
  color: var(--accent);
  letter-spacing: 0.06em;
  cursor: default;
  user-select: none;
}

.nav__links { display: flex; gap: 36px; }

.nav__links a {
  color: var(--text-muted);
  text-decoration: none;
  font-size: 12px;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  transition: color var(--transition);
  position: relative;
}

.nav__links a::after {
  content: '';
  position: absolute;
  bottom: -4px; left: 0;
  width: 0; height: 1px;
  background: var(--accent);
  transition: width var(--transition);
}

.nav__links a:hover { color: var(--accent); }
.nav__links a:hover::after { width: 100%; }

/* ─── Layout ─────────────────────────────────────────────────────────────── */
.app { position: relative; min-height: 100vh; }

.container {
  position: relative; z-index: 1;
  max-width: 1100px;
  margin: 0 auto;
  padding: 120px 48px 80px;
}

/* ─── Scroll-reveal sections ─────────────────────────────────────────────── */
section {
  margin-bottom: 120px;
  opacity: 0;
  transform: translateY(28px);
  transition: opacity 0.65s var(--ease), transform 0.65s var(--ease);
}

section.revealed {
  opacity: 1;
  transform: none;
}

/* ─── Typography ─────────────────────────────────────────────────────────── */
h1 {
  font-family: 'Syne', sans-serif;
  font-size: clamp(48px, 7vw, 88px);
  font-weight: 800;
  color: #f8fafc;
  line-height: 1.0;
  letter-spacing: -0.03em;
}

h2 {
  font-family: 'Syne', sans-serif;
  font-size: clamp(22px, 3vw, 30px);
  font-weight: 700;
  color: #f1f5f9;
  margin-bottom: 32px;
  display: flex;
  align-items: center;
  gap: 14px;
  letter-spacing: -0.01em;
}

h2::before {
  content: '';
  display: block;
  flex-shrink: 0;
  width: 4px; height: 26px;
  background: linear-gradient(180deg, var(--accent), var(--accent-2));
  border-radius: 2px;
}

h3 {
  font-family: 'Syne', sans-serif;
  font-size: 18px;
  font-weight: 600;
  color: #f1f5f9;
}

p { color: #94a3b8; line-height: 1.8; font-weight: 300; }

a { color: var(--accent); text-decoration: none; }
a:hover { text-decoration: underline; }

/* ─── Cards ──────────────────────────────────────────────────────────────── */
.card {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 28px 32px;
  transition: border-color var(--transition), background var(--transition), transform var(--transition), box-shadow var(--transition);
}

.card:hover {
  border-color: var(--border-accent);
  background: var(--bg-card-hover);
  transform: translateY(-4px);
  box-shadow: 0 16px 40px rgba(0, 0, 0, 0.4);
}

/* ─── Tags / pills ───────────────────────────────────────────────────────── */
.tag {
  display: inline-block;
  padding: 5px 14px;
  border: 1px solid var(--border);
  border-radius: 100px;
  font-size: 13px;
  font-weight: 500;
  color: var(--text-muted);
  background: rgba(255, 255, 255, 0.03);
  transition: all var(--transition);
  cursor: default;
}

.tag:hover {
  border-color: var(--accent);
  color: var(--accent);
  background: var(--accent-glow);
}

/* ─── Buttons ────────────────────────────────────────────────────────────── */
.btn {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 12px 28px;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 500;
  letter-spacing: 0.02em;
  cursor: pointer;
  transition: all var(--transition);
  text-decoration: none !important;
  border: none;
}

.btn-primary {
  background: var(--accent);
  color: #0a1628;
}

.btn-primary:hover {
  background: #7dd3fc;
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(56, 189, 248, 0.28);
}

.btn-outline {
  background: transparent;
  color: var(--accent);
  border: 1px solid var(--border-accent);
}

.btn-outline:hover {
  background: var(--accent-glow);
  transform: translateY(-2px);
}

/* ─── Utilities ──────────────────────────────────────────────────────────── */
.accent   { color: var(--accent); }
.accent-2 { color: var(--accent-2); }

.divider {
  border: none;
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--border), transparent);
  margin: 24px 0;
}

ul { padding-left: 0; list-style: none; }
li { margin-bottom: 8px; }

/* ─── Scrollbar ──────────────────────────────────────────────────────────── */
::-webkit-scrollbar { width: 5px; }
::-webkit-scrollbar-track { background: var(--bg); }
::-webkit-scrollbar-thumb { background: #1e293b; border-radius: 3px; }
::-webkit-scrollbar-thumb:hover { background: #334155; }

/* ─── Footer ─────────────────────────────────────────────────────────────── */
.footer {
  position: relative; z-index: 1;
  text-align: center;
  padding: 28px 48px;
  border-top: 1px solid var(--border);
  color: var(--text-muted);
  font-size: 13px;
}

/* ─── Responsive ─────────────────────────────────────────────────────────── */
@media (max-width: 768px) {
  .nav, .nav--scrolled { padding-left: 24px; padding-right: 24px; }
  .nav__links { gap: 20px; }
  .nav__links a { font-size: 11px; }
  .container { padding: 96px 24px 60px; }
  section { margin-bottom: 80px; }
  .footer { padding: 24px; }
}

@media (max-width: 480px) {
  .nav__links { display: none; }
}
</style>
