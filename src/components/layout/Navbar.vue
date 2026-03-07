<script setup>
import { ref, onMounted } from 'vue'

const isDark = ref(true)

const toggleDark = () => {
  isDark.value = !isDark.value
  if (isDark.value) {
    document.documentElement.classList.add('dark')
    localStorage.theme = 'dark'
  } else {
    document.documentElement.classList.remove('dark')
    localStorage.theme = 'light'
  }
}

onMounted(() => {
  if (localStorage.theme === 'dark' || (!('theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
    isDark.value = true
    document.documentElement.classList.add('dark')
  } else {
    isDark.value = false
    document.documentElement.classList.remove('dark')
  }
})
</script>

<template>
  <header
     class="sticky top-0 z-50 bg-white dark:bg-[#0B0E14] border-b border-gray-100 dark:border-transparent transition-colors duration-300"
  >
    <div class="max-w-7xl mx-auto px-6 py-6 flex items-center justify-between">
      <!-- Logo -->
      <div class="text-xl font-bold text-cyan-600 dark:text-cyan-400">
        &lt;Viron/&gt;
      </div>

      <div class="flex items-center gap-8">
        <!-- Nav links -->
        <nav class="hidden md:flex gap-8 text-sm text-gray-600 dark:text-gray-300 font-medium">
          <a href="#about" class="hover:text-black dark:hover:text-white transition">About</a>
          <a href="#Tech-Stack" class="hover:text-black dark:hover:text-white transition">Tech Stack</a>
          <a href="#experience" class="hover:text-black dark:hover:text-white transition">Experience</a>
          <a href="#Process-Timeline" class="hover:text-black dark:hover:text-white transition">Workflow</a>
          <a href="#Contact" class="hover:text-black dark:hover:text-white transition">Contact</a>
        </nav>
        
        <!-- Toggle Button -->
        <button @click="toggleDark" class="p-2 rounded-lg bg-gray-100 dark:bg-white/10 text-gray-600 dark:text-gray-300 hover:bg-gray-200 dark:hover:bg-white/20 transition-colors" aria-label="Toggle Dark Mode">
          <!-- Sun icon for dark mode (click to switch to light) -->
          <svg v-if="isDark" xmlns="http://www.w3.org/2000/svg" class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M16 12a4 4 0 11-8 0 4 4 0 018 0z" />
          </svg>
          <!-- Moon icon for light mode (click to switch to dark) -->
          <svg v-else xmlns="http://www.w3.org/2000/svg" class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z" />
          </svg>
        </button>
      </div>
    </div>
  </header>
</template>
