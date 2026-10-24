
<script setup lang="ts">
defineProps<{
  name: string
  role: string
  description: string
  image: string
}>()
</script>

<template>
  <section
      id="home"
      class="relative flex min-h-[85vh] scroll-mt-24 items-center overflow-hidden px-6 py-20"
  >
    <div class="pointer-events-none absolute left-1/2 top-1/2 -z-10 h-80 w-80 -translate-x-1/2 -translate-y-1/2 rounded-full bg-purple-700/20 blur-[120px]"></div>

    <div class="mx-auto grid w-full max-w-6xl items-center gap-12 md:grid-cols-2">
      <div>
        <p class="mb-4 font-medium text-purple-400">
          Hello there! I'm
        </p>

        <h1 class="text-5xl font-bold tracking-tight sm:text-6xl">
          {{ name }}
          <span class="text-purple-400">.</span>
        </h1>

        <h2 class="mt-4 text-xl font-medium text-gray-300 sm:text-2xl">
          {{ role }}
        </h2>

        <p class="mt-6 max-w-xl leading-8 text-gray-400">
          {{ description }}
        </p>

        <div class="mt-8 flex flex-wrap gap-4">
          <a
              href="#projects"
              class="rounded-lg bg-purple-600 px-6 py-3 font-semibold transition hover:bg-purple-500"
          >
            View My Work
          </a>

          <a
              href="#contact"
              class="rounded-lg border border-white/15 px-6 py-3 font-semibold transition hover:border-purple-400 hover:text-purple-300"
          >
            Contact Me
          </a>
        </div>

        <div class="mt-8 flex flex-wrap gap-4 text-sm text-gray-400">
          <a href="https://github.com/holldixx" target="_blank" rel="noreferrer" class="hover:text-purple-300">
            GitHub ↗
          </a>
        </div>
      </div>

      <div class="flex justify-center md:justify-end">
        <div class="relative">
          <div class="absolute -inset-3 rounded-3xl bg-purple-600/20 blur-2xl"></div>
          <img
              :src="image"
              :alt="`${name}'s profile photo`"
              class="relative h-72 w-72 rounded-3xl border border-purple-400/30 object-cover object-contain shadow-2xl shadow-purple-950/40 sm:h-96 sm:w-96"
          />
        </div>
      </div>
    </div>
  </section>
</template>