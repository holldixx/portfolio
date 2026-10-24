<script setup lang="ts">
import About from "@/components/About.vue";
import Achievements from "@/components/Achievements.vue";
import Contact from "@/components/Contact.vue";
import NavBar from "@/components/NavBar.vue";
import Profile from "@/components/Profile.vue";
import Projects from "@/components/Projects.vue";
import Skills from "@/components/Skills.vue";
import BGM from "@/components/Bgm.vue";
</script>

<template>
  <div class="min-h-screen overflow-x-hidden bg-[#09090f] text-slate-100">
    <NavBar />
    <main>
      <Profile
          name="Mike Justine Tabio"
          role=" 4th year Computer Engineering Student"
          description="I build software, explore embedded systems, and create technology-driven solutions to real-world problems."
          image="/profile2.png"
          />
      <About/>
      <Skills/>
      <Projects/>
      <Achievements/>
      <Contact/>
      <BGM/>
    </main>

    <footer class="border-t border-white/10 px-6 py-8 text-center text-sm text-gray-500">
      <p>
        © {{ new Date().getFullYear() }} Mike Justine E. Tabio. Built with Vue and Tailwind CSS.
      </p>

      <a href="#home" class="mt-3 inline-block text-purple-300 hover:text-purple-200">
        Back to top ↑
      </a>
    </footer>
  </div>
</template>