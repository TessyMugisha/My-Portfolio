<template>
    <section id="skills" class="mt-12">
    <h2 class="text-xl font-semibold text-white drop-shadow">Skills</h2>

    <div class="mt-4 grid gap-4 sm:grid-cols-2">
      <div>
        <h3 class="text-white/95 font-medium">Languages</h3>
        <div class="mt-2 flex flex-wrap gap-2">
          <span v-for="s in langs" :key="s"
                class="rounded-md bg-white/15 px-2 py-1 ring-1 ring-white/25 text-white/95 text-sm">
            {{ s }}
          </span>
        </div>
      </div>

      <div>
        <h3 class="text-white/95 font-medium">Frameworks & Tools</h3>
        <div class="mt-2 flex flex-wrap gap-2">
          <span v-for="s in tools" :key="s"
                class="rounded-md bg-white/15 px-2 py-1 ring-1 ring-white/25 text-white/95 text-sm">
            {{ s }}
          </span>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
const langs = ['TypeScript', 'JavaScript', 'Java', 'Swift', 'Python', 'SQL']
const tools = ['Vue', 'React', 'SwiftUI', 'JUnit', 'Apps Script', 'Git', 'Vite', 'Tailwind', 'Figma']
</script>
