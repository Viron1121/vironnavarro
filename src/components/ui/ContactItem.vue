<template>
  <div class="border border-gray-200 dark:border-gray-800 rounded-xl p-5 bg-white dark:bg-[#0D1117] flex items-center gap-4 hover:border-cyan-500 transition">

    <div class="w-12 h-12 rounded-lg bg-gray-50 dark:bg-[#0B0E14] border border-cyan-500 flex items-center justify-center text-cyan-600 dark:text-cyan-400">
      <component :is="icon" class="w-5 h-5"/>
    </div>

    <div>
      <p class="text-gray-500 dark:text-gray-400 text-sm">{{ label }}</p>
      <p class="text-gray-900 dark:text-white font-medium">{{ value }}</p>
    </div>

  </div>
</template>

<script setup>
defineProps({
  label: String,
  value: String,
  icon: Object
})
</script>