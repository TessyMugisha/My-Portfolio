<template>
  <section :id="sectionId" class="mt-12">
    <h2 class="text-xl font-semibold">Certifications & Programs</h2>

    <!-- uniform row height -->
    <ul class="mt-5 grid gap-6 sm:grid-cols-2 lg:grid-cols-3 auto-rows-[320px]">
      <li
        v-for="c in items"
        :key="c.id"
        class="flex flex-col rounded-lg bg-white/85 ring-1 ring-neutral-200/70
               p-6 w-full min-h-[320px]
               hover:-translate-y-0.5 hover:shadow-md hover:ring-neutral-300 transition"
      >
        <!-- Status at top -->
        <div class="mb-2">
          <span
            class="inline-flex items-center rounded-full px-2.5 py-0.5 text-xs font-medium ring-1"
            :class="statusClass(c.status)"
          >
            {{ c.status }}
          </span>
        </div>

        <!-- Title + issuer -->
        <h3 class="font-medium tracking-tight leading-snug">{{ c.title }}</h3>
        <p class="text-sm text-neutral-600">{{ c.issuer }}</p>

        <!-- Blurb only for quick items -->
        <p
          v-if="c.quick && c.blurb"
          class="mt-3 text-sm text-neutral-700 leading-relaxed"
        >
          {{ c.blurb }}
        </p>

        <!-- Footer pinned to bottom -->
        <div class="mt-auto flex flex-wrap items-center gap-3 text-xs text-neutral-600">
          <span
            v-for="t in (c.tags || [])"
            :key="t"
            class="text-neutral-500"
          >
            • {{ t }}
          </span>

          <a
            v-if="c.link"
            :href="c.link"
            target="_blank"
            rel="noopener"
            class="ml-auto rounded-md bg-neutral-900 text-white px-2 py-1 text-xs ring-1 ring-neutral-900
                   hover:-translate-y-0.5 transition"
          >
            {{ c.quick ? 'Quick Access' : 'View' }}
          </a>
        </div>
      </li>
    </ul>
  </section>
</template>

<script setup>
const props = defineProps({
  items: { type: Array, required: true },
  sectionId: { type: String, default: 'certifications' }
})

/* warm, readable status colors */
const statusClass = (status) => {
  switch ((status || '').toLowerCase()) {
    case 'completed':
      return 'bg-green-100 text-green-800 ring-green-300'
    case 'in progress':
      return 'bg-amber-100 text-amber-800 ring-amber-300'
    default:
      return 'bg-neutral-100 text-neutral-700 ring-neutral-200'
  }
}
</script>
