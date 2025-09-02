<template>
  <section id="projects" class="mt-12">
    <h2 class="text-xl font-semibold text-white drop-shadow">Projects</h2>

    <div class="mt-6 space-y-6">
      <article v-for="p in projects" :key="p.id"
               class="group rounded-2xl overflow-hidden ring-1 ring-white/30 bg-white/10 backdrop-saturate-150 hover:bg-white/15 transition">
        <div class="grid md:grid-cols-[2fr,1fr] gap-0">
          <div class="p-5">
            <h3 class="text-white text-lg font-semibold">{{ p.title }}</h3>
            <p class="text-white/85 mt-1">{{ p.subtitle }}</p>
            <div class="mt-3 flex flex-wrap gap-2 text-xs">
              <span v-for="t in p.tags" :key="t"
                    class="rounded-md bg-white/15 px-2 py-1 ring-1 ring-white/25 text-white/90">
                {{ t }}
              </span>
            </div>
            <div class="mt-4 flex gap-3">
              <button @click="openProject(p)"
                      class="rounded-md bg-neutral-900 text-white px-3 py-1.5 text-sm hover:-translate-y-0.5 transition">
                Quick view
              </button>
              <a v-if="p.links.github" :href="p.links.github" target="_blank" rel="noopener"
                 class="rounded-md bg-white text-neutral-900 px-3 py-1.5 text-sm hover:-translate-y-0.5 transition">
                GitHub
              </a>
              <a v-if="p.links.live" :href="p.links.live" target="_blank" rel="noopener"
                 class="rounded-md bg-white text-neutral-900 px-3 py-1.5 text-sm hover:-translate-y-0.5 transition">
                Live
              </a>
            </div>
          </div>
          <div class="relative">
            <img :src="p.image" :alt="p.title" class="h-full w-full object-cover md:rounded-l-none md:rounded-r-2xl">
          </div>
        </div>
      </article>
    </div>

    <!-- Modal -->
    <div v-if="activeProject" class="fixed inset-0 z-50 flex items-center justify-center p-4" role="dialog" aria-modal="true">
      <div class="absolute inset-0 bg-black/40" @click="closeProject()" aria-hidden="true"></div>
      <div ref="modalBox" class="relative w-full max-w-2xl rounded-2xl bg-white/95 shadow-xl ring-1 ring-neutral-200 focus:outline-none" tabindex="-1">
        <div class="aspect-[16/9] w-full overflow-hidden rounded-t-2xl">
          <img :src="activeProject.image" :alt="activeProject.title" class="h-full w-full object-cover" />
        </div>
        <div class="p-5">
          <div class="flex items-start justify-between gap-4">
            <h3 class="text-lg font-semibold tracking-tight">{{ activeProject.title }}</h3>
            <button ref="closeBtn" @click="closeProject()"
                    class="rounded-md px-2 py-1 text-sm ring-1 ring-neutral-300 hover:ring-neutral-400"
                    aria-label="Close">Close</button>
          </div>
          <p class="text-sm text-neutral-700 mt-1">{{ activeProject.subtitle }}</p>
          <div class="mt-4 space-y-2 text-sm leading-relaxed">
            <p><span class="font-medium">S:</span> {{ activeProject.star.s }}</p>
            <p><span class="font-medium">T:</span> {{ activeProject.star.t }}</p>
            <p><span class="font-medium">A:</span> {{ activeProject.star.a }}</p>
            <p><span class="font-medium">R:</span> {{ activeProject.star.r }}</p>
          </div>
          <div class="mt-5 flex flex-wrap gap-3">
            <a v-if="activeProject.links.github" :href="activeProject.links.github" target="_blank" rel="noopener"
               class="inline-flex items-center gap-2 rounded-lg border border-neutral-300 bg-white px-3 py-1.5 text-sm hover:-translate-y-0.5 hover:shadow-sm transition">GitHub</a>
            <a v-if="activeProject.links.live" :href="activeProject.links.live" target="_blank" rel="noopener"
               class="inline-flex items-center gap-2 rounded-lg border border-neutral-900 bg-neutral-900 px-3 py-1.5 text-sm text-white hover:-translate-y-0.5 hover:shadow-sm transition">Live Demo</a>
            <a v-if="activeProject.links.docs" :href="activeProject.links.docs" target="_blank" rel="noopener"
               class="inline-flex items-center gap-2 rounded-lg border border-neutral-300 bg-white px-3 py-1.5 text-sm hover:-translate-y-0.5 hover:shadow-sm transition">Case Study</a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, nextTick, onBeforeUnmount } from 'vue'
import shotSwiftUI     from '../assets/shots/ipad_nav_fix.jpg'
import shotCampusBuddy from '../assets/shots/campus_buddy.jpg'
import shotPOS         from '../assets/shots/java_pos.jpg'
import shotIntake      from '../assets/shots/intake_ai.webp'

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

const activeProject = ref(null)
const modalBox = ref(null)
const closeBtn = ref(null)
const onKey = (e) => { if (e.key === 'Escape') closeProject() }

const openProject = async (p) => {
  activeProject.value = p
  await nextTick()
  modalBox.value?.focus()
  closeBtn.value?.focus()
  document.addEventListener('keydown', onKey)
}
const closeProject = () => {
  activeProject.value = null
  document.removeEventListener('keydown', onKey)
}
onBeforeUnmount(() => document.removeEventListener('keydown', onKey))
</script>
