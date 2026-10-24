<script setup lang="ts">
const skillGroups = [
  {
    title: 'Frontend Development',
    skills: ['HTML', 'CSS', 'JavaScript', 'TypeScript', 'Vue.js', 'Tailwind CSS'],
  },
  {
    title: 'Programming & Backend',
    skills: ['C','C++', 'Python', 'SQL', 'Django', 'Git'],
  },
  {
    title: 'Hardware Development',
    skills: ['Arduino', 'ESP32', 'Embedded Systems', 'Electronics'],
  },
]
</script>

<template>
  <section id="skills" class="scroll-mt-24 px-6 py-24">
    <div class="mx-auto max-w-6xl">
      <p class="text-sm font-semibold uppercase tracking-[0.25em] text-purple-400">
        What I work with
      </p>

      <h2 class="mt-3 text-3xl font-bold sm:text-4xl">
        Technical Skills
      </h2>

      <div class="mt-10 grid gap-5 md:grid-cols-3">
        <article
            v-for="group in skillGroups"
            :key="group.title"
            class="rounded-2xl border border-white/10 bg-white/[0.03] p-6 transition hover:border-purple-500/50"
        >
          <h3 class="text-lg font-semibold">{{ group.title }}</h3>

          <div class="mt-5 flex flex-wrap gap-2">
            <span
                v-for="skill in group.skills"
                :key="skill"
                class="rounded-lg border border-purple-400/20 bg-purple-500/10 px-3 py-2 text-sm text-purple-200"
            >
              {{ skill }}
            </span>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>