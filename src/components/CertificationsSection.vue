<template>
  <section id="certifications" class="scroll-mt-24 mt-12">
    <h2 class="text-xl font-semibold text-white drop-shadow">Certifications & Programs</h2>
    <div class="h-1.5 w-16 rounded-full bg-amber-400 mt-3"></div>

    <!-- Nothing defined at all -->
    <p v-if="certs.length === 0" class="mt-6 text-white/80">
      No certifications yet. Add items to <code>certs</code> in this file.
    </p>

    <!-- Completed -->
    <div v-if="completed.length" class="mt-6">
      <div class="flex items-baseline gap-3">
        <h3 class="text-white/90 font-semibold">Completed</h3>
        <span class="text-xs rounded-full bg-white/12 px-2 py-0.5 ring-1 ring-white/20 text-white/80">
          {{ completed.length }}
        </span>
      </div>

      <div class="mt-3 grid gap-4 sm:grid-cols-2 lg:grid-cols-3">
        <article
          v-for="c in completed" :key="c.id"
          class="rounded-2xl bg-white/12 ring-1 ring-white/25 backdrop-blur-md p-4 hover:bg-white/15 transition"
        >
          <div class="flex items-start justify-between gap-3">
            <h4 class="text-white font-semibold leading-tight">{{ c.title }}</h4>
            <span class="shrink-0 inline-flex items-center rounded-full bg-emerald-500/15 text-emerald-100
                         ring-1 ring-emerald-400/30 px-2 py-0.5 text-[11px] font-semibold">
              ✓ Completed
            </span>
          </div>
          <p class="mt-1 text-white/80 text-sm">{{ c.issuer }}</p>
          <p v-if="c.blurb" class="mt-2 text-white/85 text-sm leading-6">{{ c.blurb }}</p>
          <div class="mt-3">
            <a v-if="c.link" :href="c.link" target="_blank" rel="noopener"
               class="inline-flex items-center gap-2 rounded-full bg-white text-neutral-900 px-3 py-1.5 text-xs font-semibold
                      ring-1 ring-white/20 hover:-translate-y-0.5 transition">
              View credential
            </a>
          </div>
        </article>
      </div>
    </div>

    <!-- In Progress -->
    <div v-if="inProgress.length" class="mt-8">
      <div class="flex items-baseline gap-3">
        <h3 class="text-white/90 font-semibold">In Progress</h3>
        <span class="text-xs rounded-full bg-white/12 px-2 py-0.5 ring-1 ring-white/20 text-white/80">
          {{ inProgress.length }}
        </span>
      </div>

      <div class="mt-3 grid gap-4 sm:grid-cols-2 lg:grid-cols-3">
        <article
          v-for="c in inProgress" :key="c.id"
          class="rounded-2xl bg-white/12 ring-1 ring-white/25 backdrop-blur-md p-4 hover:bg-white/15 transition"
        >
          <div class="flex items-start justify-between gap-3">
            <h4 class="text-white font-semibold leading-tight">{{ c.title }}</h4>
            <span class="shrink-0 inline-flex items-center rounded-full bg-amber-400/15 text-amber-200
                         ring-1 ring-amber-400/30 px-2 py-0.5 text-[11px] font-semibold">
              • In Progress
            </span>
          </div>
          <p class="mt-1 text-white/80 text-sm">{{ c.issuer }}</p>
          <p v-if="c.blurb" class="mt-2 text-white/85 text-sm leading-6">{{ c.blurb }}</p>
          <div class="mt-3 h-1.5 w-full rounded-full bg-white/10 overflow-hidden">
            <div class="h-full bg-amber-400/80" :style="{ width: (c.progress ?? 30) + '%' }"></div>
          </div>
          <p class="mt-1 text-xs text-white/70">~{{ c.progress ?? 30 }}% complete</p>
        </article>
      </div>
    </div>

    <!-- Fallback: if statuses don't match, show everything ungrouped -->
    <div v-if="!completed.length && !inProgress.length && certs.length" class="mt-6">
      <p class="text-white/80 text-sm">
        Showing all items (status didn’t match <code>Completed</code> / <code>In Progress</code>).
      </p>
      <div class="mt-3 grid gap-4 sm:grid-cols-2 lg:grid-cols-3">
        <article
          v-for="c in certs" :key="c.id"
          class="rounded-2xl bg-white/12 ring-1 ring-white/25 backdrop-blur-md p-4"
        >
          <h4 class="text-white font-semibold leading-tight">{{ c.title }}</h4>
          <p class="mt-1 text-white/80 text-sm">{{ c.issuer }}</p>
          <p v-if="c.blurb" class="mt-2 text-white/85 text-sm leading-6">{{ c.blurb }}</p>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'

const certs = ref([
  // Completed
  { id: 'google-pm-foundations', title: 'Foundations of Project Management', issuer: 'Google (Coursera)', status: 'Completed', blurb: 'Explored PM fundamentals to evaluate if PM is a fit for me.', link: '' },
  { id: 'att-tech-academy', title: 'AT&T Technology Academy', issuer: 'AT&T', status: 'Completed', blurb: 'Broad exposure to technology roles (SE, PM, data).', link: '' },
  { id: 'asana-project-work', title: 'Asana — Certified Project Work', issuer: 'Asana', status: 'Completed', blurb: 'Managed tasks, timelines, and cross-team collaboration.', link: '' },
  { id: 'ncl-spring-2024', title: 'National Cyber League — Spring 2024 (Individual Game)', issuer: 'NCL', status: 'Completed', blurb: 'Hands-on intro to cybersecurity (crypto, forensics, OSINT).', link: '' },

  // In Progress
  { id: 'ibm-skillsbuild-ai', title: 'IBM SkillsBuild — AI Literacy', issuer: 'IBM', status: 'In Progress', blurb: 'Practical AI literacy and hands-on fundamentals.', progress: 55, link: '' },
  { id: 'oracle-university', title: 'Oracle University — Learning Path', issuer: 'Oracle', status: 'In Progress', blurb: 'Exploring Oracle ecosystem topics.', progress: 30, link: '' }
])

const completed  = computed(() => certs.value.filter(c => c.status === 'Completed'))
const inProgress = computed(() => certs.value.filter(c => c.status === 'In Progress'))
</script>
