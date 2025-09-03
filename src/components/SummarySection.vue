<template>
  <section
    id="summary"
    class="relative scroll-mt-24 min-h-[90vh] py-16 lg:py-24 text-white"
  >
    <div class="mx-auto max-w-6xl px-4">

      <!-- === HERO ACTION (glass resume pill) === -->
      <div class="relative">
        <a
          href="https://docs.google.com/document/d/1goHncsZmfnskWUtYJVqu5T78h9gQ_hbo39Iar-ZJL3Q/edit?tab=t.0"
          target="_blank" rel="noopener"
          class="absolute right-0 -top-3 sm:-top-2 inline-flex items-center gap-2
                 rounded-full bg-white/12 px-6 py-3 font-semibold text-white
                 ring-1 ring-white/25 backdrop-blur-md shadow
                 hover:bg-white/15 hover:-translate-y-0.5 transition will-change-transform"
        >
          My Resume
        </a>
      </div>

      <div class="mt-2 flex flex-wrap items-start gap-10">
        <div class="grow">

          <!-- Open to work (glass badge + pulsing dot) -->
          <span class="inline-flex items-center gap-2 rounded-full bg-emerald-500/15
                       text-emerald-100 ring-1 ring-emerald-400/30 px-3 py-1 backdrop-blur-md">
            <span class="relative flex h-3 w-3">
              <span class="absolute inline-flex h-full w-full rounded-full bg-emerald-400/80 opacity-75 animate-ping"></span>
              <span class="relative inline-flex h-3 w-3 rounded-full bg-emerald-400 ring-2 ring-emerald-300/40"></span>
            </span>
            <span class="text-xs font-semibold tracking-wide">OPEN TO WORK</span>
          </span>

          <p class="mt-5 text-amber-400 font-semibold tracking-[.18em]">SOFTWARE ENGINEER</p>
          <h1 class="mt-3 text-5xl sm:text-6xl font-extrabold leading-tight drop-shadow">
            Tessy Mugisha
          </h1>

          <p class="mt-6 max-w-2xl text-white/95 text-lg leading-8 drop-shadow">
            Senior @ <span class="font-semibold">Oklahoma Christian University</span> (CS + AI).
            I build smarter systems with
            <em class="text-amber-300 not-italic">creativity</em>,
            <em class="text-amber-300 not-italic">empathy</em>, and
            <em class="text-amber-300 not-italic">curiosity</em>.
          </p>

          <!-- Contact row (glass chips) -->
          <div class="mt-8 grid gap-4 sm:grid-cols-2 max-w-2xl">
            <a href="mailto:mugishatessy@gmail.com"
               class="inline-flex items-center gap-3 rounded-2xl bg-white/12 p-4
                      ring-1 ring-white/25 backdrop-blur-md hover:bg-white/15 transition">
              <img src="/logos/email.png" alt="" class="h-5 w-5 opacity-90"> mugishatessy@gmail.com
            </a>
            <a href="tel:+14057466609"
               class="inline-flex items-center gap-3 rounded-2xl bg-white/12 p-4
                      ring-1 ring-white/25 backdrop-blur-md hover:bg-white/15 transition">
              📞 +1-405-746-6609
            </a>
            <a href="https://www.linkedin.com/in/tessy-mugisha-5334ba173/" target="_blank" rel="noopener"
               class="inline-flex items-center gap-3 rounded-2xl bg-white/12 p-4
                      ring-1 ring-white/25 backdrop-blur-md hover:bg-white/15 transition">
              <img src="/logos/linkedin.png" alt="" class="h-5 w-5 opacity-90"> linkedin.com
            </a>
            <div class="inline-flex items-center gap-3 rounded-2xl bg-white/12 p-4
                        ring-1 ring-white/25 backdrop-blur-md">
              📍 Oklahoma City, OK
            </div>
          </div>
        </div>
      </div>

      <!-- === UNDER-HERO SUMMARY CONTENT === -->
      <div class="mt-16 mx-auto max-w-4xl">
        <h2 class="text-5xl sm:text-6xl font-extrabold text-amber-400 drop-shadow">Summary</h2>
        <div class="h-1.5 w-16 rounded-full bg-amber-400 mt-3"></div>

        <!-- Glass card around the paragraphs -->
        <div class="mt-8 rounded-2xl bg-white/10 ring-1 ring-white/15 backdrop-blur-md p-6 md:p-7">
          <div class="space-y-7 md:space-y-8 leading-8 text-white/95 drop-shadow">
            <p>
              ✨ Hi, I’m <strong class="font-bold">Tessy</strong>, a senior Computer Science &amp; AI student pursuing my
              graduate degree in AI (expected May 2026). Originally from Kigali, Rwanda, I’ve had the chance to work at
              <span class="font-semibold text-amber-300/90">American Fidelity</span> and
              <span class="font-semibold text-amber-300/90">Compassion International</span>, where I’ve grown as both a
              technologist and a team player.
            </p>

            <p>
              I’m passionate about creating smarter systems, blending tech with creativity, and bringing a
              bubbly, positive energy into everything I do.
            </p>

            <p>
              Fun fact: if money or time weren’t an issue, I’d be an archaeologist. I’m absolutely fascinated
              by history and love exploring the stories hidden in the past.
            </p>
          </div>
        </div>

        <!-- Strengths + DiSC block (already glass; kept as-is with a small boost) -->
        <div class="mt-6 rounded-2xl bg-white/08 backdrop-blur-md ring-1 ring-white/12 p-5 sm:p-6">
          <div class="pl-4 border-l-4 border-amber-400/90">
            <p class="font-semibold">Here are my Top 5 Clifton Strengths 💪🏾</p>
            <ul class="mt-3 space-y-2">
              <li class="flex gap-3">
                <span class="mt-2 h-1.5 w-1.5 rounded-full bg-amber-400"></span>
                <span><strong>Relator</strong> — Thrive on building meaningful connections and achieving goals together.</span>
              </li>
              <li class="flex gap-3">
                <span class="mt-2 h-1.5 w-1.5 rounded-full bg-amber-400"></span>
                <span><strong>Empathy</strong> — Step into others’ shoes to understand and serve better.</span>
              </li>
              <li class="flex gap-3">
                <span class="mt-2 h-1.5 w-1.5 rounded-full bg-amber-400"></span>
                <span><strong>Deliberative</strong> — Anticipate challenges and make thoughtful decisions.</span>
              </li>
              <li class="flex gap-3">
                <span class="mt-2 h-1.5 w-1.5 rounded-full bg-amber-400"></span>
                <span><strong>Connectedness</strong> — Believe everything has purpose and meaning.</span>
              </li>
              <li class="flex gap-3">
                <span class="mt-2 h-1.5 w-1.5 rounded-full bg-amber-400"></span>
                <span><strong>Developer</strong> — Spot and nurture potential in people.</span>
              </li>
            </ul>

            <div class="mt-6">
              <p class="font-semibold">DiSC Working Style</p>
              <span class="mt-2 inline-flex items-center rounded-full bg-amber-400/15 text-amber-200
                             ring-1 ring-amber-400/30 px-2 py-0.5 text-xs font-medium">
                CD
              </span>
              <ul class="mt-3 space-y-2">
                <li class="flex gap-3">
                  <span class="mt-2 h-1.5 w-1.5 rounded-full bg-amber-400"></span>
                  <span>Questioning &amp; logic-driven</span>
                </li>
                <li class="flex gap-3">
                  <span class="mt-2 h-1.5 w-1.5 rounded-full bg-amber-400"></span>
                  <span>Objective &amp; skeptical (in a constructive way :))</span>
                </li>
                <li class="flex gap-3">
                  <span class="mt-2 h-1.5 w-1.5 rounded-full bg-amber-400"></span>
                  <span>Challenge ideas to spark stronger solutions</span>
                </li>
              </ul>
            </div>
          </div>
        </div>
        <!-- /block -->
      </div>
      <!-- === /UNDER-HERO SUMMARY CONTENT === -->
    </div>
  </section>
</template>

<script setup>
// no script needed
</script>
