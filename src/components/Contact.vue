<script setup lang="ts">
import { Github, Twitch, Mail, MapPin } from 'lucide-vue-next'
const contact = {
  email: 'mikejustinetabio@gmail.com',
  location: 'Lal-lo, Cagayan',
  github: 'https://github.com/holldixx',
  twitch: 'https://www.twitch.tv/tayyn_n',
}
</script>

<template>
  <section id="contact" class="scroll-mt-24 px-6 py-24">
    <div class="mx-auto max-w-4xl">
      <p class="text-sm font-semibold uppercase tracking-[0.25em] text-purple-400">
        Let's connect
      </p>

      <h2 class="mt-3 text-3xl font-bold sm:text-4xl">
        Contact Me
      </h2>

      <p class="mt-5 max-w-2xl leading-7 text-gray-400">
        Have a project idea, collaboration opportunity, or question?
        Feel free to reach out.
      </p>

      <div class="mt-8 grid gap-4 sm:grid-cols-2">

        <a
            :href="`mailto:${contact.email}`"
            class="group flex items-center gap-4 rounded-2xl border border-white/10 bg-white/[0.03] p-5 transition hover:border-purple-500/50 hover:bg-purple-500/5"
        >
          <div class="rounded-xl bg-purple-500/10 p-3 text-purple-400 transition group-hover:bg-purple-500/20">
            <Mail :size="24" />
          </div>
          <div class="min-w-0">
            <p class="text-sm text-gray-400">Email</p>
            <p class="mt-2 break-all font-medium text-purple-300">
              {{ contact.email }}
            </p>
          </div>
        </a>

        <div
            class="flex items-center gap-4 rounded-2xl border border-white/10 bg-white/[0.03] p-5"
        >
          <div class="rounded-xl bg-purple-500/10 p-3 text-purple-400">
            <MapPin :size="24" />
          </div>
          <div>
            <p class="text-sm text-gray-400">Location</p>
            <p class="mt-2 font-medium text-purple-300">{{ contact.location }}</p>
          </div>
        </div>

        <a
            :href="contact.github"
            target="_blank"
            rel="noopener noreferrer"
            aria-label="Visit my GitHub profile"
            class="group flex items-center gap-4 rounded-2xl border border-white/10 bg-white/[0.03] p-5 transition hover:border-purple-500/50 hover:bg-purple-500/5"
        >
          <div class="rounded-xl bg-purple-500/10 p-3 text-purple-400 transition group-hover:bg-purple-500/20">
            <Github :size="24" />
          </div>
          <div>
            <p class="text-sm text-gray-400">GitHub</p>
            <p class="mt-2 font-medium text-purple-300">
              View my profile ↗
            </p>
          </div>
        </a>

        <a
            :href="contact.twitch"
            target="_blank"
            rel="noopener noreferrer"
            aria-label="Visit my Twitch channel"
            class="group flex items-center gap-4 rounded-2xl border border-white/10 bg-white/[0.03] p-5 transition hover:border-purple-500/50 hover:bg-purple-500/5"
        >
          <div class="rounded-xl bg-purple-500/10 p-3 text-purple-400 transition group-hover:bg-purple-500/20">
            <Twitch :size="24" />
          </div>
          <div>
            <p class="text-sm text-gray-400">Twitch</p>
            <p class="mt-2 font-medium text-purple-300">
              I stream sometimes ^_^ ↗
            </p>
          </div>
        </a>
      </div>
    </div>
  </section>
</template>