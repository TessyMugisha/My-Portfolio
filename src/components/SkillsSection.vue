<template>
  <section id="skills" class="scroll-mt-24 mt-12">
    <h2 class="text-xl font-semibold text-white drop-shadow">Skills</h2>
    <div class="h-1.5 w-16 rounded-full bg-amber-400 mt-3"></div>

    <div class="mt-6 grid gap-5 sm:grid-cols-2 xl:grid-cols-4">
      <!-- Languages -->
      <div class="rounded-2xl bg-white/12 ring-1 ring-white/25 backdrop-blur-md p-5">
        <h3 class="text-white/95 font-semibold tracking-wide">Languages</h3>
        <div class="mt-3 flex flex-wrap gap-2">
          <span v-for="s in langs" :key="s"
            class="rounded-md bg-white/12 px-2 py-1 ring-1 ring-white/20 text-white/95 text-sm">
            {{ s }}
          </span>
        </div>
      </div>

      <!-- Software Development -->
      <div class="rounded-2xl bg-white/12 ring-1 ring-white/25 backdrop-blur-md p-5">
        <h3 class="text-white/95 font-semibold tracking-wide">Software Development</h3>
        <div class="mt-3 flex flex-wrap gap-2">
          <span v-for="s in devTools" :key="s"
            class="rounded-md bg-white/12 px-2 py-1 ring-1 ring-white/20 text-white/95 text-sm">
            {{ s }}
          </span>
        </div>
      </div>

      <!-- Project Management -->
      <div class="rounded-2xl bg-white/12 ring-1 ring-white/25 backdrop-blur-md p-5">
        <h3 class="text-white/95 font-semibold tracking-wide">Project Management</h3>
        <div class="mt-3 flex flex-wrap gap-2">
          <span v-for="s in pmTools" :key="s"
            class="rounded-md bg-white/12 px-2 py-1 ring-1 ring-white/20 text-white/95 text-sm">
            {{ s }}
          </span>
        </div>
      </div>

      <!-- UX Design -->
      <div class="rounded-2xl bg-white/12 ring-1 ring-white/25 backdrop-blur-md p-5">
        <h3 class="text-white/95 font-semibold tracking-wide">UX Design</h3>
        <div class="mt-3 flex flex-wrap gap-2">
          <span v-for="s in uxTools" :key="s"
            class="rounded-md bg-white/12 px-2 py-1 ring-1 ring-white/20 text-white/95 text-sm">
            {{ s }}
          </span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
// Keep what you actually use. Tweak freely.

// Languages you code in
const langs = [
  'TypeScript', 'JavaScript', 'Java', 'Swift', 'Python', 'SQL', 'HTML', 'CSS','Bash'
]

// Software dev stack (frameworks, runtimes, tooling)
const devTools = [
  'Vue 3', 'React', 'Tailwind CSS', 'Vite', 'Vue Router',
  'SwiftUI', 'Xcode',
  'Node.js', 'Express',
  'JUnit',
  'Git & GitHub'
]

// Project management tools & workflows you know
const pmTools = [
  'Asana (Certified)', 'Jira', 'Trello', 'Notion',
  'Kanban', 'Scrum', 'Roadmapping', 'Stakeholder Comms', 'Rally', 'Confluence'
  ,'Agile Methodology',
]

// UX design tools & practices
const uxTools = [
  'Figma', 'Framer',
  'Wireframing', 'Prototyping', 'Usability Testing',
  'Design Systems', 'Accessibility'
]
</script>
