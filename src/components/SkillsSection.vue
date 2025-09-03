<template>
  <section id="skills" class="mt-12">
    <h2 class="text-xl font-semibold text-white drop-shadow">Skills</h2>

    <div class="mt-4 grid gap-4 sm:grid-cols-2">
      <!-- Languages -->
      <div>
        <h3 class="text-white/95 font-medium">Languages</h3>
        <div class="mt-2 flex flex-wrap gap-2">
          <span v-for="s in langs" :key="s"
                class="rounded-md bg-white/15 px-2 py-1 ring-1 ring-white/25 text-white/95 text-sm">
            {{ s }}
          </span>
        </div>
      </div>

      <!-- Frameworks & Tools -->
      <div>
        <h3 class="text-white/95 font-medium">Frameworks &amp; Tools</h3>
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

<script setup>
// Put what YOU actually use. This is a good starter for your stack.
const langs = [
  'TypeScript', 'JavaScript', 'Java', 'Swift', 'Python', 'SQL'
]

// Mix of frameworks, libraries, platform tools you’ve used in your projects
const tools = [
  // Frontend
  'Vue 3', 'React', 'Tailwind CSS', 'Vite', 'Vue Router',
  // State/Testing (add if you use them)
  'Pinia', 'Vitest', 'Jest',
  // Mobile
  'SwiftUI', 'Xcode',
  // Backend/Runtime
  'Node.js', 'Express',
  // Automation/Cloud
  'Google Apps Script', 'Vercel',
  // Testing/Quality
  'JUnit',
  // Design/Collab
  'Figma', 'Git & GitHub'
]
</script>
