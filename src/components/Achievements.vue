<script setup lang="ts">
import { ref } from 'vue'
import { Trophy, Brain, Medal, X, ChevronLeft, ChevronRight } from 'lucide-vue-next'

const achievements = [
  {
    title: 'Regional ITE Convention',
    detail: 'Champion Robotics-Sumobot',
    year: '2026',
    icon: Trophy,
    images: [
      '/achievements/ite-1.jpg',
      '/achievements/ite-2.jpg',
      '/achievements/ite-3.jpg',
      '/achievements/ite-4.jpg',
      '/achievements/ite-5.jpg',
      '/achievements/ite-6.jpg',
      '/achievements/ite-7.jpg',
    ],
  },
  {
    title: 'CPEYESTA Quiz Bowl',
    detail: 'Department Champion for Quiz Bowl Competition',
    year: '2025',
    icon: Brain,
    images: [
        '/achievements/qb-1.jpg',
        '/achievements/qb-2.jpg',
    ],
  },
  {
    title: 'COEA Days Baseball',
    detail: '3rd place for baseball competition',
    year: '2025',
    icon: Medal,
    images: [
        'achievements/bb-1.jpg',
        'achievements/bb-2.jpg',
        'achievements/bb-3.jpg',
    ],
  },
]

const selectedAchievement = ref<(typeof achievements)[number] | null>(null)

function closeGallery() {
  selectedAchievement.value = null
}
</script>

<template>
  <section id="achievements" class="scroll-mt-24 px-6 py-24">
    <div class="mx-auto max-w-4xl">
      <p class="text-sm font-semibold uppercase tracking-[0.25em] text-purple-400">
        Milestones
      </p>

      <h2 class="mt-3 text-3xl font-bold sm:text-4xl">
        Achievements
      </h2>

      <p class="mt-4 text-gray-400">
        A collection of competitions, experiences, and milestones.
        Click an achievement to view its gallery.
      </p>

      <div class="mt-10 space-y-4">
        <button
            v-for="item in achievements"
            :key="item.title"
            type="button"
            @click="selectedAchievement = item"
            class="group flex w-full items-center gap-4 rounded-2xl border border-white/10 bg-white/[0.03] p-6 text-left transition hover:border-purple-500/60 hover:bg-purple-500/[0.06]"
        >
          <div
              class="flex h-12 w-12 shrink-0 items-center justify-center rounded-xl bg-purple-500/15 text-purple-300 transition group-hover:bg-purple-500/25"
          >
            <component :is="item.icon" :size="24" />
          </div>

          <div class="min-w-0 flex-1">
            <div class="flex flex-wrap items-center justify-between gap-2">
              <h3 class="font-semibold text-white">
                {{ item.title }}
              </h3>

              <span class="text-sm text-purple-300">
                {{ item.year }}
              </span>
            </div>

            <p class="mt-2 text-sm leading-6 text-gray-400">
              {{ item.detail }}
            </p>

            <p class="mt-3 text-xs font-medium text-purple-400">
              View photos →
            </p>
          </div>
        </button>
      </div>
    </div>

    <Teleport to="body">
      <Transition name="gallery">
        <div
            v-if="selectedAchievement"
            class="fixed inset-0 z-50 flex items-center justify-center bg-black/80 p-4 backdrop-blur-sm"
            @click.self="closeGallery"
            @keydown.esc="closeGallery"
        >
          <div
              role="dialog"
              aria-modal="true"
              :aria-label="selectedAchievement.title + ' photo gallery'"
              class="relative w-full max-w-4xl overflow-hidden rounded-2xl border border-white/10 bg-[#11111b] shadow-2xl shadow-purple-950/30"
          >

            <div class="flex items-start justify-between gap-4 border-b border-white/10 p-5 sm:p-6">
              <div>
                <p class="text-xs font-semibold uppercase tracking-[0.2em] text-purple-400">
                  {{ selectedAchievement.year }} • Photo Gallery
                </p>

                <h3 class="mt-2 text-xl font-bold text-white sm:text-2xl">
                  {{ selectedAchievement.title }}
                </h3>

                <p class="mt-2 text-sm text-gray-400">
                  {{ selectedAchievement.detail }}
                </p>
              </div>

              <button
                  type="button"
                  @click="closeGallery"
                  aria-label="Close gallery"
                  class="shrink-0 rounded-xl border border-white/10 p-2 text-gray-400 transition hover:bg-white/10 hover:text-white"
              >
                <X :size="22" />
              </button>
            </div>

            <div class="p-5 sm:p-6">
              <div class="mb-3 flex items-center justify-between text-xs text-gray-500">
                <span>{{ selectedAchievement.images.length }} photos</span>
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
                    v-for="(photo, index) in selectedAchievement.images"
                    :key="photo"
                    class="w-[85%] shrink-0 snap-center sm:w-[70%] md:w-[60%]"
                >
                  <img
                      :src="photo"
                      :alt="`${selectedAchievement.title} photo ${index + 1}`"
                      class="aspect-[4/3] w-full rounded-xl border border-white/10 bg-white/5 object-contain"
                  />

                  <p class="mt-2 text-center text-xs text-gray-500">
                    Photo {{ index + 1 }} of {{ selectedAchievement.images.length }}
                  </p>
                </div>
              </div>
            </div>

            <div class="flex justify-end border-t border-white/10 p-4">
              <button
                  type="button"
                  @click="closeGallery"
                  class="rounded-xl bg-purple-600 px-5 py-2.5 text-sm font-semibold text-white transition hover:bg-purple-500"
              >
                Close Gallery
              </button>
            </div>
          </div>
        </div>
      </Transition>
    </Teleport>
  </section>
</template>

<style scoped>
.gallery-enter-active,
.gallery-leave-active {
  transition: opacity 0.2s ease;
}

.gallery-enter-active > div,
.gallery-leave-active > div {
  transition: transform 0.2s ease;
}

.gallery-enter-from,
.gallery-leave-to {
  opacity: 0;
}

.gallery-enter-from > div,
.gallery-leave-to > div {
  transform: translateY(12px) scale(0.98);
}
</style>