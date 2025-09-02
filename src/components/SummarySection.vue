<template>
  <section id="summary" class="min-h-[86vh] grid items-center text-white">
    <div class="mx-auto max-w-6xl">
      <div class="relative">
        <a href="https://docs.google.com/document/d/1goHncsZmfnskWUtYJVqu5T78h9gQ_hbo39Iar-ZJL3Q/edit?tab=t.0"
           target="_blank" rel="noopener"
           class="absolute right-0 -top-2 rounded-full bg-amber-400 px-6 py-3 font-semibold text-neutral-900
                  shadow-lg ring-1 ring-black/10 hover:-translate-y-0.5 transition">
          My Resume
        </a>
      </div>

      <div class="flex flex-wrap items-center gap-8">
        <div class="grow">
          <div class="flex items-center gap-2">
            <span class="inline-block h-2 w-2 rounded-full bg-emerald-400"></span>
            <span class="text-sm/none">Open to work</span>
          </div>

          <p class="mt-4 text-amber-400 font-semibold tracking-[.18em]">SOFTWARE ENGINEER</p>
          <h1 class="mt-2 text-5xl sm:text-6xl font-extrabold leading-tight drop-shadow">Tessy Mugisha</h1>

          <p class="mt-5 max-w-2xl text-white/95 text-lg drop-shadow">
            Senior @ <span class="font-semibold">Oklahoma Christian University</span> (CS + AI).
            I build smarter systems with <em class="text-amber-300 not-italic">creativity</em>,
            <em class="text-amber-300 not-italic">empathy</em>, and <em class="text-amber-300 not-italic">curiosity</em>.
          </p>

          <!-- Contact row -->
          <div class="mt-6 grid gap-3 sm:grid-cols-2 max-w-2xl">
            <a href="mailto:mugishatessy@gmail.com"
               class="inline-flex items-center gap-3 rounded-xl bg-white/10 p-3 ring-1 ring-white/20 hover:bg-white/15 transition">
              <img src="/logos/email.png" alt="" class="h-5 w-5 opacity-90"> mugishatessy@gmail.com
            </a>
            <a href="tel:+14057466609"
               class="inline-flex items-center gap-3 rounded-xl bg-white/10 p-3 ring-1 ring-white/20 hover:bg-white/15 transition">
              📞 +1-405-746-6609
            </a>
            <a href="https://www.linkedin.com/in/tessy-mugisha-5334ba173/" target="_blank" rel="noopener"
               class="inline-flex items-center gap-3 rounded-xl bg-white/10 p-3 ring-1 ring-white/20 hover:bg-white/15 transition">
              <img src="/logos/linkedin.png" alt="" class="h-5 w-5 opacity-90"> linkedin.com/in/…
            </a>
            <div class="inline-flex items-center gap-3 rounded-xl bg-white/10 p-3 ring-1 ring-white/20">
              📍 Oklahoma City, OK
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
