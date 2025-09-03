<template>
  <section id="experience" class="scroll-mt-24 py-16 lg:py-24 text-white">
    <div class="mx-auto max-w-6xl px-4">
      <!-- Heading -->
      <h2 class="text-[clamp(2rem,5vw,3.5rem)] font-extrabold drop-shadow">
        Work Experience
      </h2>
      <div class="h-1.5 w-16 rounded-full bg-amber-400 mt-3"></div>

      <!-- Timeline / cards -->
      <ol class="mt-10 space-y-6">
        <li
          v-for="job in jobs"
          :key="job.id"
          class="rounded-2xl bg-black/30 ring-1 ring-white/10 backdrop-blur-md p-6 md:p-7"
        >
          <!-- Top row -->
          <div class="flex flex-col gap-1 sm:flex-row sm:items-baseline sm:justify-between">
            <div class="flex items-center gap-2">
              <span
                class="inline-flex items-center rounded-full bg-amber-400/15 text-amber-200
                       ring-1 ring-amber-400/30 px-2 py-0.5 text-[11px] font-semibold uppercase tracking-wide"
              >
                {{ job.badge }}
              </span>
              <h3 class="text-xl font-semibold leading-tight">
                {{ job.role }}
              </h3>
            </div>
            <span class="text-sm text-white/70">{{ job.dates }}</span>
          </div>

          <!-- Company -->
          <p class="mt-1 text-white/90 font-medium">{{ job.company }}</p>

          <!-- STAR -->
          <div class="mt-4 grid gap-2 leading-7 text-white/95">
            <p><span class="font-semibold">Situation/Task:</span> {{ job.st }}</p>
            <p><span class="font-semibold">Action:</span> {{ job.action }}</p>
            <p><span class="font-semibold">Result:</span> {{ job.result }}</p>
            <p v-if="job.extra" class="pt-3 mt-1 border-t border-white/10">
              <span class="font-semibold">Extra Impact:</span> {{ job.extra }}
            </p>
          </div>
        </li>
      </ol>
    </div>
  </section>
</template>

<script setup>
const jobs = [
  {
    id: 'compassion',
    role: 'Software Engineer ',
    dates: 'May 2025 – Aug 2025',
    company: 'Compassion International',
    st: 'Joined the Creative Solutions engineering team to improve the iPad version of the MyCompassion app, where navigation glitches and inconsistent UI were impacting user experience.',
    action:
      'Collaborated with 2+ developers and project managers, building reusable React components, fixing high-priority UI/UX bugs, and aligning with designers to ensure consistency across the app.',
    result:
      'Reduced recurring navigation issues by 30%, boosted development speed by 20% through scalable components, and improved overall design system consistency.',
    extra:
      'Led a passion project on personalization and engagement, gathering user insights and data. I presented my findings to the CIO and senior leadership, influencing discussions on future supporter engagement strategies.',
  },
  {
    id: 'af',
    role: 'IT Operations ',
    dates: 'Jan 2025 – May 2025',
    company: 'American Fidelity',
    st: 'Departments relied on IT Operations to resolve system and access issues quickly, as delays impacted business continuity.',
    action:
      'Partnered with IT staff to analyze, document, and resolve 20–30 support tickets weekly, providing step-by-step updates to non-technical users and escalating complex cases as needed.',
    result:
      'Achieved a 90%+ resolution rate within SLA, reduced downtime for multiple departments, and earned positive feedback from staff and leadership for reliability and communication. Recognized with an extended role offer to continue supporting IT Operations.',
  },
  {
    id: 'extern',
    role: 'Student Ambassador',
    dates: 'Oct 2024 – Dec 2024',
    company: 'Extern',
    st: 'I gained valuable experience through Extern that helped me land internships, but realized that many students at my non-target school were unaware of these opportunities.',
    action:
      'I hosted info sessions, partnered with student clubs and career services, and shared my story during class visits and tabling events, highlighting how externships build real-world skills and career opportunities.',
    result:
      'I reached 50+ students and increased campus awareness of Extern by 15%, which led to more applications and participation.',
  },
]
</script>
