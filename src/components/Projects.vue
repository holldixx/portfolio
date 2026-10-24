<script setup lang="ts">
import { ref } from 'vue'
import { X, ChevronLeft, ChevronRight, FolderCode } from 'lucide-vue-next'

const projects = [
  {
    title: 'ESP32 Fan Monitoring System',
    category: 'IoT • Embedded Systems',
    description:
        'An embedded monitoring project that collects environmental and fan-status data and displays the information in a mobile application.',
    image: '/projects/fan-monitor.jpg',
    tags: ['ESP32', 'Flutter', 'Sensors'],
    media: [
      '/projects/fan1.jpg',
      '/projects/fan2.jpg',
      '/projects/fan3.jpg',
    ],
  },
  {
    title: 'TapatKalusugan',
    category: 'Website • Fullstack Development',
    description:
        'A scheduling appointment website for children vaccination and a vaccine inventory management system.',
    image: '/projects/web1.jpg',
    tags: ['HTML', 'CSS', 'JavaScript', 'PHP'],
    media: [
      '/projects/web2.jpg',
      '/projects/web3.jpg',
    ],
  },
  {
    title: 'PIC Development Board',
    category: 'Embedded Systems',
    description:
        'A PIC training board designed for embedded systems projects, hands-on experiments, and lectures.',
    image: '/projects/PIC.jpg',
    tags: ['Electronics', 'PIC Microcontroller'],
    media: [
      '/projects/PIC1.jpg',
      '/projects/PIC2.jpg',
      '/projects/PIC3.jpg',
      '/projects/PIC4.jpg',
      '/projects/PIC5.jpg',
    ],
  },
] as const

type Project = (typeof projects)[number]

const selectedProject = ref<Project | null>(null)

function closeProject() {
  selectedProject.value = null
}
</script>

<template>
  <section id="projects" class="scroll-mt-24 px-6 py-24">
    <div class="mx-auto max-w-6xl">
      <p class="text-sm font-semibold uppercase tracking-[0.25em] text-purple-400">
        What I've been building
      </p>

      <h2 class="mt-3 text-3xl font-bold sm:text-4xl">
        Featured Projects
      </h2>

      <p class="mt-4 text-gray-400">
        A selection of my work in software development and embedded systems.
        Click a project to explore more.
      </p>

      <div class="mt-10 grid gap-6 md:grid-cols-2 lg:grid-cols-3">
        <button
            v-for="project in projects"
            :key="project.title"
            type="button"
            @click="selectedProject = project"
            class="group overflow-hidden rounded-2xl border border-white/10 bg-white/[0.03] text-left transition hover:-translate-y-1 hover:border-purple-500/50 hover:bg-purple-500/[0.04]"
        >
          <div class="relative overflow-hidden">
            <img
                :src="project.image"
                :alt="project.title"
                class="h-48 w-full bg-white/5 object-contain transition duration-300 group-hover:scale-105"
                loading="lazy"
            />

            <div
                class="absolute inset-0 flex items-center justify-center bg-black/40 opacity-0 transition group-hover:opacity-100"
            >
              <div
                  class="flex items-center gap-2 rounded-full bg-purple-600 px-4 py-2 text-sm font-semibold text-white"
              >
                <FolderCode :size="18" />
                View Project
              </div>
            </div>
          </div>

          <div class="p-6">
            <p class="text-xs font-medium uppercase tracking-wider text-purple-400">
              {{ project.category }}
            </p>

            <h3 class="mt-3 text-xl font-bold text-white">
              {{ project.title }}
            </h3>

            <p class="mt-3 text-sm leading-7 text-gray-400">
              {{ project.description }}
            </p>

            <div class="mt-5 flex flex-wrap gap-2">
              <span
                  v-for="tag in project.tags"
                  :key="tag"
                  class="rounded-md bg-white/5 px-2.5 py-1 text-xs text-gray-300"
              >
                {{ tag }}
              </span>
            </div>

            <p class="mt-5 text-xs font-medium text-purple-400">
              View photos →
            </p>
          </div>
        </button>
      </div>
    </div>

    <Teleport to="body">
      <Transition name="project-modal">
        <div
            v-if="selectedProject"
            class="fixed inset-0 z-50 flex items-center justify-center overflow-y-auto bg-black/80 p-4 backdrop-blur-sm"
            @click.self="closeProject"
            @keydown.esc="closeProject"
        >
          <div
              role="dialog"
              aria-modal="true"
              :aria-label="selectedProject.title + ' project details'"
              class="relative my-auto w-full max-w-4xl overflow-hidden rounded-2xl border border-white/10 bg-[#11111b] shadow-2xl shadow-purple-950/30"
          >
            <div
                class="flex items-start justify-between gap-4 border-b border-white/10 p-5 sm:p-6"
            >
              <div>
                <p class="text-xs font-semibold uppercase tracking-[0.2em] text-purple-400">
                  {{ selectedProject.category }}
                </p>

                <h3 class="mt-2 text-xl font-bold text-white sm:text-2xl">
                  {{ selectedProject.title }}
                </h3>

                <p class="mt-2 max-w-2xl text-sm leading-6 text-gray-400">
                  {{ selectedProject.description }}
                </p>
              </div>

              <button
                  type="button"
                  @click="closeProject"
                  aria-label="Close project"
                  class="shrink-0 rounded-xl border border-white/10 p-2 text-gray-400 transition hover:bg-white/10 hover:text-white"
              >
                <X :size="22" />
              </button>
            </div>

            <div class="p-5 sm:p-6">
              <div
                  class="mb-3 flex items-center justify-between gap-3 text-xs text-gray-500"
              >
                <span>{{ selectedProject.media.length }} photos</span>

                <span class="flex items-center gap-1">
                  <ChevronLeft :size="15" />
                  Scroll sideways
                  <ChevronRight :size="15" />
                </span>
              </div>

              <div
                  class="flex snap-x snap-mandatory gap-4 overflow-x-auto overscroll-x-contain pb-4"
              >
                <div
                    v-for="(photo, index) in selectedProject.media"
                    :key="photo"
                    class="w-[85%] shrink-0 snap-center sm:w-[70%] md:w-[60%]"
                >
                  <img
                      :src="photo"
                      :alt="`${selectedProject.title} photo ${index + 1}`"
                      class="aspect-[4/3] w-full rounded-xl border border-white/10 bg-white/5 object-contain"
                      loading="lazy"
                  />

                  <p class="mt-2 text-center text-xs text-gray-500">
                    Photo {{ index + 1 }} of {{ selectedProject.media.length }}
                  </p>
                </div>
              </div>
            </div>

            <div class="border-t border-white/10 px-5 py-4 sm:px-6">
              <p class="mb-3 text-xs font-semibold uppercase tracking-wider text-gray-500">
                Technologies used
              </p>

              <div class="flex flex-wrap gap-2">
                <span
                    v-for="tag in selectedProject.tags"
                    :key="tag"
                    class="rounded-md bg-purple-500/10 px-3 py-1.5 text-xs text-purple-300"
                >
                  {{ tag }}
                </span>
              </div>
            </div>

            <div class="flex justify-end border-t border-white/10 p-4">
              <button
                  type="button"
                  @click="closeProject"
                  class="rounded-xl bg-purple-600 px-5 py-2.5 text-sm font-semibold text-white transition hover:bg-purple-500"
              >
                Close Project
              </button>
            </div>
          </div>
        </div>
      </Transition>
    </Teleport>
  </section>
</template>

<style scoped>
.project-modal-enter-active,
.project-modal-leave-active {
  transition: opacity 0.2s ease;
}

.project-modal-enter-active > div,
.project-modal-leave-active > div {
  transition: transform 0.2s ease;
}

.project-modal-enter-from,
.project-modal-leave-to {
  opacity: 0;
}

.project-modal-enter-from > div,
.project-modal-leave-to > div {
  transform: translateY(12px) scale(0.98);
}
</style>