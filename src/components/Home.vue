<template>
  <div class="relative">
    <!-- Site-wide fixed background -->
    <div class="site-bg" aria-hidden="true"></div>

    <!-- Sticky bottom nav (scroll-spy) -->
<nav
  class="fixed left-1/2 -translate-x-1/2 bottom-6 z-[60] px-2 py-2
         rounded-full ring-1 ring-white/15 shadow-xl
         bg-gradient-to-r from-black/30 via-black/25 to-black/30
         backdrop-blur-md">
  <ul class="flex items-center gap-1">
    <li v-for="s in sections" :key="s.id">
      <a
        :href="'#' + s.id"
        class="group flex items-center gap-2 px-4 py-2 rounded-full transition
               font-semibold"
        :class="activeSection === s.id
          ? 'bg-white text-neutral-900 shadow-[0_4px_16px_rgba(0,0,0,.18)]'
          : 'text-white/90 hover:text-white hover:bg-white/10'"
      >
        <span aria-hidden="true">{{ s.icon }}</span>
        <span>{{ s.label }}</span>
      </a>
    </li>
  </ul>
</nav>


    <!-- Page sections -->
    <main class="relative z-10 mx-auto max-w-6xl px-6 py-10">
      <SummarySection class="will-reveal" />
      <ExperienceSection class="will-reveal" />
      <ProjectsSection class="will-reveal" />
      <SkillsSection class="will-reveal" />
      <CertificationsSection/>
      <LinksSection class="will-reveal" />
      <footer class="mt-14 mb-2 text-sm text-white/90 will-reveal">
        <div class="text-center drop-shadow">
          <p class="italic text-md">“Seek first the kingdom of God and all will be added to you” — Mt 6:33</p>
          <p class="italic text-md mt-1">Build with Purpose</p>
          <p class="mt-3 text-sm">© {{ new Date().getFullYear() }} Tessy Mugisha</p>
        </div>
      </footer>
    </main>

    <!-- Back to top -->
    <button
      v-show="showToTop"
      @click="scrollToTop"
      class="fixed bottom-5 right-5 z-50 rounded-full bg-neutral-900 text-white p-3 shadow-lg ring-1 ring-black/10 hover:-translate-y-0.5 transition"
      aria-label="Back to top">
      ↑
    </button>
  </div>
</template>



<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

// import the section components from the same folder
import SummarySection    from './SummarySection.vue'
import ExperienceSection from './ExperienceSection.vue'
import ProjectsSection   from './ProjectsSection.vue'
import SkillsSection     from './SkillsSection.vue'
import CertificationsSection from './CertificationsSection.vue'
import LinksSection      from './LinksSection.vue'

/* Back to top */
const showToTop = ref(false)
const onScroll = () => { showToTop.value = window.scrollY > 500 }
const scrollToTop = () => window.scrollTo({ top: 0, behavior: 'smooth' })

/* Reveal on scroll */
let io
const installReveal = () => {
  const nodes = document.querySelectorAll('.will-reveal')
  io = new IntersectionObserver((entries) => {
    entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('reveal-in'); io.unobserve(e.target) } })
  }, { rootMargin: '0px 0px -10% 0px', threshold: 0.1 })
  nodes.forEach(n => io.observe(n))
}

/* Scroll-spy for bottom nav */
const sections = ref([
  { id:'summary',   label:'Summary',    icon:'👤' },
  { id:'experience',label:'Experience', icon:'💼' },
  { id:'projects',  label:'Projects',   icon:'📃' },
  { id:'skills',    label:'Skills',     icon:'💻' },
  { id:'certifications',    label:'certs',     icon:'📋' },
])
const activeSection = ref('summary')
let spy
const installSpy = () => {
  const targets = sections.value.map(s => document.getElementById(s.id)).filter(Boolean)
  spy = new IntersectionObserver((entries) => {
    entries.forEach(e => { if (e.isIntersecting) activeSection.value = e.target.id })
  }, { rootMargin: '-30% 0px -50% 0px', threshold: 0.2 })
  targets.forEach(t => spy.observe(t))
}

onMounted(() => {
  window.addEventListener('scroll', onScroll, { passive: true })
  installReveal()
  installSpy()
})
onBeforeUnmount(() => {
  window.removeEventListener('scroll', onScroll)
  io?.disconnect()
  spy?.disconnect()
})
</script>

<style>
html { scroll-behavior: smooth; }

/* Full-page fixed background */
.site-bg {
  position: fixed;
  inset: 0;
  z-index: -10;
  background: url('/logos/tessyimage.jpg') center / cover no-repeat fixed;
  pointer-events: none; /* don't block clicks */
}

/* Dark glassy overlay on top of the image */
.site-bg::after {
  content: "";
  position: absolute;
  inset: 0;
  pointer-events: none;
  background:
    radial-gradient(1000px 650px at 12% 10%, rgba(0,0,0,.24), transparent 60%),
    linear-gradient(180deg, rgba(0,0,0,.20) 0%, rgba(0,0,0,.12) 55%, rgba(0,0,0,.08) 100%);
}



/* Reveal motion
.will-reveal { opacity: 0; transform: translateY(10px); }
.reveal-in   { opacity: 1; transform: none; transition: opacity .5s ease, transform .5s ease; }
@media (prefers-reduced-motion: reduce) {
  * { transition: none !important; animation-duration: 0.001ms !important; animation-iteration-count: 1 !important; }
  .will-reveal { opacity: 1 !important; transform: none !important; }
} */
</style>

