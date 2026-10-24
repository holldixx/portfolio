<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount } from 'vue'
import { Volume2, VolumeX } from 'lucide-vue-next'

const audio = ref<HTMLAudioElement | null>(null)
const isPlaying = ref(false)

async function toggleMusic() {
  if (!audio.value) return

  if (isPlaying.value) {
    audio.value.pause()
    isPlaying.value = false
    return
  }

  try {
    await audio.value.play()
    isPlaying.value = true
  } catch (error) {
    console.error('Unable to play background music:', error)
    isPlaying.value = false
  }
}

function handleAudioPause() {
  isPlaying.value = false
}

onMounted(() => {
  audio.value?.addEventListener('pause', handleAudioPause)
})

onBeforeUnmount(() => {
  audio.value?.removeEventListener('pause', handleAudioPause)
})
</script>

<template>
  <div>
    <audio
        ref="audio"
        src="/bgm/bgm.mp3"
        loop
        preload="none"
    />

    <button
        type="button"
        @click="toggleMusic"
        :aria-label="isPlaying ? 'Pause background music' : 'Play background music'"
        :title="isPlaying ? 'Pause music' : 'Play music'"
        class="fixed bottom-6 right-6 z-40 flex items-center gap-2 rounded-full border border-purple-400/30 bg-[#11111b]/90 px-4 py-3 text-purple-300 shadow-lg shadow-purple-950/30 backdrop-blur-md transition hover:border-purple-400 hover:bg-purple-600 hover:text-white"
    >
      <Volume2 v-if="isPlaying" :size="20" />
      <VolumeX v-else :size="20" />

      <span class="text-sm font-medium">
        {{ isPlaying ? 'Music On' : 'Music Off' }}
      </span>
    </button>
  </div>
</template>