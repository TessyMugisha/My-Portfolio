<template>
  <div class="relative">
    <!-- Background (soft neutrals, no white overlay) -->
    <div class="fixed inset-0 -z-10 overflow-hidden" aria-hidden="true">
      <!-- Base gradient with a warm radial glow -->
      <div
        class="absolute inset-0"
        style="
          background:
            radial-gradient(1100px 700px at 15% 10%, rgba(243, 221, 190, 0.45), transparent 60%),
            linear-gradient(180deg, #f3e7d3 0%, #fff7e9 55%, #fffdf8 100%);
        "
      ></div>

      <!-- Subtle animated wavy lines -->
      <svg class="absolute inset-0 waves opacity-15" width="100%" height="100%" viewBox="0 0 1440 800" preserveAspectRatio="none">
        <g class="wave-group">
          <path d="M0,120 C180,80 360,160 540,120 C720,80 900,160 1080,120 C1260,80 1440,140 1440,140"
                fill="none" stroke="#a49786" stroke-width="0.6"/>
          <path d="M0,260 C180,220 360,300 540,260 C720,220 900,300 1080,260 C1260,220 1440,280 1440,280"
                fill="none" stroke="#a49786" stroke-width="0.5"/>
          <path d="M0,400 C180,360 360,440 540,400 C720,360 900,440 1080,400 C1260,360 1440,420 1440,420"
                fill="none" stroke="#a49786" stroke-width="0.5"/>
          <path d="M0,540 C180,500 360,580 540,540 C720,500 900,580 1080,540 C1260,500 1440,560 1440,560"
                fill="none" stroke="#a49786" stroke-width="0.4"/>
        </g>
      </svg>
    </div>

    <!-- Main content -->
    <main class="relative z-10 mx-auto max-w-6xl px-6 py-10 text-neutral-900">
      <!-- Header -->
      <header class="flex flex-wrap items-center gap-5">
      <img :src="portraitImg" alt="Portrait of Tessy" class="w-16 h-16 rounded-full object-cover ring-2 ring-white/80" />

        <div>
          <h1 class="text-3xl font-bold tracking-tight">Tessy Pauline Mugisha</h1>
          <p class="text-lg italic text-green-700">software engineer</p>
        </div>
      </header>

      <!-- Hero -->
      <section class="mt-8 space-y-3 text-neutral-900">
        <p class="text-xl">
          Senior @ <span class="text-blue-700 font-semibold">Oklahoma Christian University</span> (CS + AI) • Engineer-in-training
        </p>
        <p class="text-xl">
          I build smarter systems with <span class="italic text-orange-600">creativity + empathy + curiosity</span>.
        </p>

        <!-- Primary actions -->
        <nav class="mt-3 flex flex-wrap sm:flex-nowrap gap-4 items-center">
          <a href="https://tessymugisha.framer.website/" target="_blank" rel="noopener"
             class="group inline-flex items-center gap-2 px-4 py-2 rounded-lg border
                    ring-1 ring-neutral-200 bg-white/90 backdrop-blur-sm transition
                    hover:-translate-y-0.5 hover:shadow-sm hover:border-neutral-400
                    focus:outline-none focus-visible:ring-2 focus-visible:ring-neutral-800">
            <span class="font-medium">Framer Website</span>
            <svg class="size-4 transition-transform group-hover:translate-x-0.5" viewBox="0 0 24 24" fill="none" stroke="currentColor">
              <path d="M7 17L17 7M17 7H8M17 7v9" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </a>

          <a href="#projects"
             class="group inline-flex items-center gap-2 px-4 py-2 rounded-lg border border-neutral-300 bg-white/90 backdrop-blur-sm transition
                    hover:-translate-y-0.5 hover:shadow-sm hover:border-neutral-400 focus:outline-none focus-visible:ring-2 focus-visible:ring-neutral-800">
            <span class="font-medium">View Projects</span>
            <span class="h-px w-5 bg-neutral-400 transition-all group-hover:w-7"></span>
          </a>

          <a href="#writing"
             class="group inline-flex items-center gap-2 px-4 py-2 rounded-lg border border-neutral-300 bg-white/90 backdrop-blur-sm transition
                    hover:-translate-y-0.5 hover:shadow-sm hover:border-neutral-400 focus:outline-none focus-visible:ring-2 focus-visible:ring-neutral-800">
            <span class="font-medium">Writing & Updates</span>
            <span class="h-px w-5 bg-neutral-400 transition-all group-hover:w-7"></span>
          </a>

          <a href="https://docs.google.com/document/d/1goHncsZmfnskWUtYJVqu5T78h9gQ_hbo39Iar-ZJL3Q/edit?tab=t.0"
             target="_blank" rel="noopener"
             class="group inline-flex items-center gap-2 px-4 py-2 rounded-lg
                    border border-[rgb(22,163,74)] bg-[rgb(22,163,74)] text-white transition
                    hover:-translate-y-0.5 hover:shadow-sm hover:bg-[rgb(21,128,61)]
                    focus:outline-none focus-visible:ring-2 focus-visible:ring-[rgb(21,128,61)]">
            <span class="font-medium">Resume</span>
            <svg class="size-4 transition-transform group-hover:translate-x-0.5" viewBox="0 0 24 24" fill="none" stroke="currentColor">
              <path d="M7 17L17 7M17 7H8M17 7v9" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </a>
        </nav>
      </section>

      <!-- Projects -->
      <section id="projects" class="mt-12">
        <h2 class="text-xl font-semibold">Selected Projects</h2>

        <div class="mt-5 grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
          <!-- project cards -->
          <article
            v-for="p in projects"
            :key="p.id"
            class="group relative rounded-xl overflow-hidden bg-white/90 ring-1 ring-neutral-200 transition hover:-translate-y-1 hover:shadow-md hover:ring-neutral-300"
          >
            <img :src="p.image" :alt="p.title + ' screenshot'" class="w-full h-44 object-cover" />

            <div class="pointer-events-none absolute inset-0 bg-black/0 group-hover:bg-black/10 transition"></div>
            <button
              @click="openProject(p)"
              class="absolute right-3 top-3 opacity-0 group-hover:opacity-100 transition pointer-events-auto
                     rounded-lg bg-white/90 px-3 py-1.5 text-sm font-medium ring-1 ring-neutral-300 hover:ring-neutral-400"
              aria-label="Quick view"
            >
              Quick view
            </button>

            <div class="p-4">
              <h3 class="font-medium tracking-tight">{{ p.title }}</h3>
              <p class="text-sm text-neutral-700 mt-1 line-clamp-2">{{ p.subtitle }}</p>
              <div class="mt-3 flex flex-wrap gap-2 text-xs text-neutral-600">
                <span
                  v-for="t in p.tags"
                  :key="t"
                  class="rounded-md bg-neutral-100 px-2 py-1 ring-1 ring-neutral-200"
                >{{ t }}</span>
              </div>
            </div>
          </article>

          <!-- 🚧 Coming soon card -->
          <article
            class="flex h-full min-h-44 flex-col items-center justify-center rounded-xl
                   border-2 border-dashed border-neutral-300 bg-white/70 p-6 text-center"
          >
            <p class="text-sm text-neutral-700 italic">
              🚧 Coming soon: 2+ new projects
            </p>
          </article>
        </div>
      </section>

      <!-- Certifications (component) -->
      <Certifications :items="certs" />

      <!-- Writing -->
      <section id="writing" class="mt-12">
        <h2 class="text-xl font-semibold">Writing & Updates</h2>
        <p class="text-neutral-700 mt-2">Weekly progress logs + reflections on learning and building.</p>
        <ul class="mt-4 space-y-3">
          <li>
            <a href="https://medium.com/@mugishatessy" target="_blank" rel="noopener"
               class="group block rounded-lg px-3 py-2 bg-white/80 ring-1 ring-neutral-200 hover:bg-white hover:ring-neutral-300 transition
                      focus:outline-none focus-visible:ring-2 focus-visible:ring-neutral-900">
              <span class="font-medium">Progress: Entry One</span>
              <span class="block text-sm text-neutral-600 group-hover:underline">
                A Technologist’s Progress and Learning
              </span>
            </a>
          </li>
        </ul>
      </section>

<!-- Links row -->
<section aria-labelledby="links-title" class="mt-10">
  <h2 id="links-title" class="text-2xl font-semibold text-center">Find me on the internet</h2>
  <ul class="mt-4 flex justify-center gap-6">
    <li>
      <a href="https://www.linkedin.com/in/tessy-mugisha-5334ba173/" target="_blank" rel="noopener"
         aria-label="LinkedIn" title="LinkedIn"
         class="inline-flex items-center p-2 focus:outline-none focus-visible:ring-2 focus-visible:ring-blue-600">
        <img src="/logos/linkedin.png" alt="LinkedIn"
             class="h-6 w-6 opacity-80 hover:opacity-100 hover:scale-105 active:scale-95 transition" />
      </a>
    </li>

    <li>
      <a href="https://github.com/tessymugisha" target="_blank" rel="noopener"
         aria-label="GitHub" title="GitHub"
         class="inline-flex items-center p-2 focus:outline-none focus-visible:ring-2 focus-visible:ring-neutral-900">
        <img src="/logos/github.png"  alt="GitHub"
             class="h-6 w-6 opacity-80 hover:opacity-100 hover:scale-105 active:scale-95 transition" />
      </a>
    </li>

    <li>
      <a href="https://medium.com/@mugishatessy" target="_blank" rel="noopener"
         aria-label="Medium" title="Medium"
         class="inline-flex items-center p-2 focus:outline-none focus-visible:ring-2 focus-visible:ring-neutral-900">
        <img src="/logos/medium.png" alt="Medium"
             class="h-6 w-6 opacity-80 hover:opacity-100 hover:scale-105 active:scale-95 transition" />
      </a>
    </li>

    <li>
      <a href="https://www.youtube.com/@HeyTesssyy" target="_blank" rel="noopener"
         aria-label="YouTube" title="YouTube"
         class="inline-flex items-center p-2 focus:outline-none focus-visible:ring-2 focus-visible:ring-red-600">
        <img src="/logos/youtube.png" alt="YouTube" 
             class="h-6 w-6 opacity-80 hover:opacity-100 hover:scale-105 active:scale-95 transition" />
      </a>
    </li>

    <li>
      <a href="mailto:mugishatessy@gmail.com" aria-label="Email" title="Email"
         class="inline-flex items-center p-2 focus:outline-none focus-visible:ring-2 focus-visible:ring-emerald-600">
       <img src="/logos/email.png"   alt="Email"
             class="h-6 w-6 opacity-80 hover:opacity-100 hover:scale-105 active:scale-95 transition" />
      </a>
    </li>
  </ul>
</section>


      <!-- Footer -->
      <footer class="mt-14 mb-2 text-sm text-neutral-600">
        <div class="text-center">
          <p class="italic text-md text-neutral-700">“Seek first the kingdom of God and all will be added to you” — Mt 6:33</p>
          <p class="italic text-md text-neutral-600 mt-1">Build with Purpose</p>
          <p class="mt-3 text-sm text-neutral-500">© {{ new Date().getFullYear() }} Tessy Mugisha</p>
        </div>
      </footer>
    </main>

    <!-- Project Modal -->
    <div v-if="activeProject" class="fixed inset-0 z-50 flex items-center justify-center p-4" role="dialog" aria-modal="true">
      <div class="absolute inset-0 bg-black/40 backdrop-blur-md" @click="closeProject()" aria-hidden="true"></div>
      <div class="relative w-full max-w-2xl rounded-2xl bg-white/95 shadow-xl ring-1 ring-neutral-200">
        <div class="aspect-[16/9] w-full overflow-hidden rounded-t-2xl">
          <img :src="activeProject.image" :alt="activeProject.title" class="h-full w-full object-cover" />
        </div>
        <div class="p-5">
          <div class="flex items-start justify-between gap-4">
            <h3 class="text-lg font-semibold tracking-tight">{{ activeProject.title }}</h3>
            <button @click="closeProject()"
                    class="rounded-md px-2 py-1 text-sm ring-1 ring-neutral-300 hover:ring-neutral-400"
                    aria-label="Close">Close</button>
          </div>
          <p class="text-sm text-neutral-700 mt-1">{{ activeProject.subtitle }}</p>
          <div class="mt-4 space-y-2 text-sm leading-relaxed">
            <p><span class="font-medium">S (Situation):</span> {{ activeProject.star.s }}</p>
            <p><span class="font-medium">T (Task):</span> {{ activeProject.star.t }}</p>
            <p><span class="font-medium">A (Action):</span> {{ activeProject.star.a }}</p>
            <p><span class="font-medium">R (Result):</span> {{ activeProject.star.r }}</p>
          </div>
          <div class="mt-5 flex flex-wrap gap-3">
            <a v-if="activeProject.links.github" :href="activeProject.links.github" target="_blank" rel="noopener"
               class="inline-flex items-center gap-2 rounded-lg border border-neutral-300 bg-white px-3 py-1.5 text-sm
                      hover:-translate-y-0.5 hover:shadow-sm transition">GitHub</a>
            <a v-if="activeProject.links.live" :href="activeProject.links.live" target="_blank" rel="noopener"
               class="inline-flex items-center gap-2 rounded-lg border border-neutral-900 bg-neutral-900 px-3 py-1.5 text-sm text-white
                      hover:-translate-y-0.5 hover:shadow-sm transition">Live Demo</a>
            <a v-if="activeProject.links.docs" :href="activeProject.links.docs" target="_blank" rel="noopener"
               class="inline-flex items-center gap-2 rounded-lg border border-neutral-300 bg-white px-3 py-1.5 text-sm
                      hover:-translate-y-0.5 hover:shadow-sm transition">Case Study</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'


/* images */
import portraitImg      from '../assets/shots/portrait.jpg'
import shotSwiftUI from '../assets/shots/ipad_nav_fix.jpg'
import shotCampusBuddy from '../assets/shots/campus_buddy.jpg'
import shotPOS from '../assets/shots/java_pos.jpg'
import shotIntake from '../assets/shots/intake_ai.webp'





const projects = ref([
  {
    id: 'swiftui-nav-fix',
    title: 'iPad App — SwiftUI Nav Fix',
    subtitle: 'Refactored NavigationStack; unblocked deployment & restored reliable navigation.',
    image: shotSwiftUI,
    tags: ['SwiftUI', 'Xcode', 'QA', 'Internship'],
    star: {
      s: 'iPad sponsor app had unstable navigation causing dead-ends and back-stack bugs.',
      t: 'Identify root cause, implement a stable nav pattern, and ship a fix without regressions.',
      a: 'Audited push/pop flows, replaced nested NavigationStacks with a single source of truth; added state-driven routes and regression tests.',
      r: 'Crashes eliminated; navigation reliability restored; release unblocked and shipped successfully.'
    },
    links: { github: '', live: '', docs: '' }
  },
  {
    id: 'campus-buddy',
    title: 'Campus Buddy — React + AI',
    subtitle: 'Guides freshmen/transfer/international students; AI Q&A + component-driven architecture.',
    image: shotCampusBuddy,
    tags: ['React', 'TypeScript', 'LLM', 'Team work'],
    star: {
      s: 'New/transfer/international students struggled to find answers across scattered sources.',
      t: 'Design a friendly Q&A experience with reliable info and modular UI.',
      a: 'Built typed React components, prompt guardrails, and quick actions; onboard flow and FAQ seeds.',
      r: 'Faster task completion in tests; clearer path to campus rollout.'
    },
    links: { github: 'https://github.com/TessyMugisha/CampusBuddy_V1', live: '', docs: '' }
  },
  {
    id: 'pos-java',
    title: 'POS System — Java UI + Tests',
    subtitle: 'Requirements → UI → finance logic; unit-tested core flows.',
    image: shotPOS,
    tags: ['Java', 'JUnit', 'MVC'],
    star: {
      s: 'Student store needed a simple POS with discounts and receipts.',
      t: 'Design UI and implement core checkout logic with test coverage.',
      a: 'Modeled entities, wrote controllers for cart/discount/tax; created JUnit tests for edge cases.',
      r: 'All critical paths covered; demo processed orders reliably with readable receipts and logs.'
    },
    links: { github: 'https://github.com/TessyMugisha/pos-system', live: '', docs: '' }
  },
  {
    id: 'intake-ai',
    title: 'QR Intake + AI Routing',
    subtitle: 'Google Form → Sheet pipeline with AI triage for Support Central.',
    image: shotIntake,
    tags: ['Apps Script', 'Automation', 'UX'],
    star: {
      s: 'Front desk faced spikes of students; manual triage slowed lines.',
      t: 'Streamline info capture and route students faster.',
      a: 'QR to Form; Apps Script to normalize entries; added optional AI suggestions for routing and FAQs.',
      r: 'Shorter wait times and clearer handoffs; foundation for analytics dashboard.'
    },
    links: { github: '', live: '', docs: '' }
  }
])

/* ===== Certifications data ===== */
const certs = ref([
  {
    id: 'google-pm-foundations',
    title: 'Foundations of Project Management',
    issuer: 'Google (Coursera)',
    status: 'Completed',
    blurb: 'Explored PM fundamentals to evaluate if PM is a fit for me.',
    link: '',
    quick: true
  },
  {
    id: 'att-tech-academy',
    title: 'AT&T Technology Academy',
    issuer: 'AT&T',
    status: 'Completed',
    blurb: 'Broad exposure to technology roles (SE, PM, data) to get my feet wet.',
    link: ''
  },
  {
    id: 'asana-project-work',
    title: 'Asana — Certified Project Work',
    issuer: 'Asana',
    status: 'Completed',
    blurb: 'Learned a new tool to manage tasks, timelines, and cross-team collaboration.',
    link: ''
  },
  {
    id: 'ncl-spring-2024',
    title: 'National Cyber League — Spring 2024 (Individual Game)',
    issuer: 'NCL',
    status: 'Completed',
    blurb: 'Hands-on intro to cybersecurity challenges (crypto, forensics, OSINT).',
    link: ''
  },
  {
    id: 'ibm-skillsbuild-ai',
    title: 'IBM SkillsBuild — AI Literacy',
    issuer: 'IBM',
    status: 'In Progress',
    blurb: 'Building practical AI literacy and hands-on fundamentals to support a future AI master’s.',
    link: ''
  },
  {
    id: 'oracle-university',
    title: 'Oracle University — Learning Path',
    issuer: 'Oracle',
    status: 'In Progress',
    blurb: 'Exploring Oracle ecosystem topics; deciding which path to pursue next.',
    link: ''
  }
])

const activeProject = ref(null)
const openProject = (p) => { activeProject.value = p }
const closeProject = () => { activeProject.value = null }

/* Medium handler (optional helper) */
const MEDIUM_URL = 'https://medium.com/@mugishatessy'
const goToMedium = () => {
  const writingSection = document.getElementById('writing')
  if (writingSection) {
    writingSection.scrollIntoView({ behavior: 'smooth' })
    setTimeout(() => window.open(MEDIUM_URL, '_blank'), 800)
  } else {
    window.open(MEDIUM_URL, '_blank')
  }
}

/* Close modal with Esc */
const onKey = (e) => { if (e.key === 'Escape') closeProject() }
onMounted(() => window.addEventListener('keydown', onKey))
onBeforeUnmount(() => window.removeEventListener('keydown', onKey))
</script>

<style>
@media (prefers-reduced-motion: reduce) {
  * { transition: none !important; animation-duration: 0.001ms !important; animation-iteration-count: 1 !important; }
}
</style>
