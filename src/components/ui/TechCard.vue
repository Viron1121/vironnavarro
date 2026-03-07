<template>
  <div
    class="relative border border-gray-200 dark:border-white/10 p-6
           bg-gradient-to-br from-gray-50 dark:from-white/5 to-transparent
           hover:border-cyan-500/40 dark:hover:border-cyan-400/40 transition"
  >
    <h3 class="text-cyan-600 dark:text-cyan-400 text-sm tracking-widest uppercase mb-6">
      {{ title }}
    </h3>

    <div class="flex flex-wrap gap-3">
      <span
        v-for="item in items"
        :key="item"
        class="px-4 py-2 text-sm rounded
               border border-cyan-200 dark:border-cyan-400/30
               text-gray-700 dark:text-white bg-cyan-50 dark:bg-cyan-400/10"
      >
        {{ item }}
      </span>
    </div>
  </div>
</template>

<script setup>
defineProps({
  title: String,
  items: Array,
})
</script>
