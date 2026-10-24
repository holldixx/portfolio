<script setup lang="ts">
const links = [
  { label: 'About', href: '#about' },
  { label: 'Skills', href: '#skills' },
  { label: 'Projects', href: '#projects' },
  { label: 'Achievements', href: '#achievements' },
  { label: 'Contact', href: '#contact' },
]
</script>

<template>
  <header class="sticky top-0 z-50 border-b border-white/10 bg-[#09090f]/90 backdrop-blur-xl">
    <nav class="mx-auto flex max-w-6xl items-center justify-between px-6 py-4">
      <a href="#home" class="text-xl font-bold tracking-tight">
        <span class="text-purple-400">&lt;</span>
        Le Portfolio
        <span class="text-purple-400">/&gt;</span>
      </a>

      <div class="hidden items-center gap-6 md:flex">
        <a
            v-for="link in links"
            :key="link.href"
            :href="link.href"
            class="text-sm text-gray-400 transition hover:text-purple-300"
        >
          {{ link.label }}
        </a>
      </div>

      <a
          href="src/TabioCV.pdf"
          download="My-CV.pdf"
          class="rounded-lg bg-purple-600 px-4 py-2 text-sm font-semibold transition hover:bg-purple-500"
      >
        Download CV
      </a>
    </nav>

    <div class="flex gap-5 overflow-x-auto px-6 pb-3 md:hidden">
      <a
          v-for="link in links"
          :key="link.href"
          :href="link.href"
          class="shrink-0 text-sm text-gray-400 hover:text-purple-300"
      >
        {{ link.label }}
      </a>
    </div>
  </header>
</template>