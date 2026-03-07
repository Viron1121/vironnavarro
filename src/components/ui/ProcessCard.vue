<template>
  <div class="relative flex items-start group pb-12 last:pb-0">
    
    <!-- Timeline Vertical Line (handled primarily by parent, but card needs structure) -->
    <!-- Icon circle Container-->
    <div class="absolute left-0 top-0 flex items-center justify-center w-12 h-12 bg-gray-50 dark:bg-[#0B0E14] z-10">
      <div class="w-12 h-12 rounded-full border-2 border-cyan-800 dark:border-cyan-800 flex items-center justify-center bg-gray-50 dark:bg-[#0B0E14] group-hover:border-cyan-500 transition-colors duration-300 shadow-[0_0_15px_rgba(6,182,212,0.15)] group-hover:shadow-[0_0_20px_rgba(6,182,212,0.4)]">
        <component :is="icon" class="w-5 h-5 text-cyan-600 dark:text-cyan-400"/>
      </div>
    </div>

    <!-- Content box -->
    <div class="ml-24 flex-1 border border-gray-200 dark:border-white/5 rounded-xl p-6 bg-white dark:bg-[#0D1117]/80 backdrop-blur-sm group-hover:border-cyan-500/30 transition-all duration-300">
      
      <div class="flex flex-col md:flex-row md:justify-between md:items-center gap-4 mb-4">
        <h3 class="text-xl font-bold tracking-wide">{{ title }}</h3>
        <span v-if="badge" class="text-cyan-600 dark:text-cyan-500 text-xs px-3 py-1 border border-cyan-800 dark:border-cyan-800/60 rounded flex-shrink-0">
          {{ badge }}
        </span>
      </div>

      <p class="text-gray-600 dark:text-gray-400 text-sm leading-relaxed">
        {{ description }}
      </p>
    </div>
  </div>
</template>

<script setup>
defineProps({
  title: String,
  description: String,
  badge: String,
  icon: Object // Vue component for icon
})
</script>