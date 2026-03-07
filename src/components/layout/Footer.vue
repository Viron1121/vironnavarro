<template>
  <footer class="bg-gray-50 dark:bg-[#0B0E14] border-t border-gray-200 dark:border-gray-800 transition-colors duration-300">
    <div class="max-w-7xl mx-auto px-6 py-12 flex flex-col md:flex-row items-center justify-between">
      
      <!-- Brand & Copyright -->
      <div class="mb-6 md:mb-0 text-center md:text-left">
        <div class="text-xl font-bold text-cyan-600 dark:text-cyan-400 mb-2">
          &lt;Viron/&gt;
        </div>
        <p class="text-gray-500 dark:text-gray-400 text-sm">
          &copy; {{ currentYear }} Viron. All rights reserved.
        </p>
      </div>

      <!-- Links -->
      <div class="flex gap-6 text-sm text-gray-600 dark:text-gray-400">
        <a href="https://github.com/Viron1121" target="_blank" rel="noopener noreferrer" class="hover:text-cyan-600 dark:hover:text-cyan-400 transition">
          GitHub
        </a>
        <a href="https://linkedin.com/in/viron-navarro-182704287" target="_blank" rel="noopener noreferrer" class="hover:text-cyan-600 dark:hover:text-cyan-400 transition">
          LinkedIn
        </a>
        <a href="mailto:viron3210@gmail.com" target="_blank" rel="noopener noreferrer" class="hover:text-cyan-600 dark:hover:text-cyan-400 transition">
          Email
        </a>
      </div>

    </div>
  </footer>
</template>

<script setup>
import { computed } from 'vue'

const currentYear = computed(() => new Date().getFullYear())
</script>
