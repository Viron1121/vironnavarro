<script setup>
import { computed } from 'vue'

const props = defineProps({
  project: {
    type: Object,
    required: true
  }
})

const emit = defineEmits(['click'])

const handleClick = () => {
    emit('click', props.project)
}
</script>

<template>
  <div 
    @click="handleClick"
    class="group cursor-pointer flex flex-col h-full bg-white dark:bg-[#161B22] border border-gray-200 dark:border-gray-800 rounded-2xl overflow-hidden hover:border-cyan-500/50 dark:hover:border-cyan-500/50 transition-all duration-300 hover:shadow-[0_0_30px_rgba(6,182,212,0.1)] hover:-translate-y-1"
  >
    <!-- Image Header -->
    <div class="relative h-48 w-full overflow-hidden bg-gray-100 dark:bg-gray-800">
        <!-- Optional: Replace src with actual project image later -->
        <img 
            v-if="project.image" 
            :src="project.image" 
            :alt="project.title"
            class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500"
        />
        <div v-else class="w-full h-full flex items-center justify-center text-gray-400 dark:text-gray-500">
            <span class="text-sm">Image Placeholder</span>
        </div>
        
        <!-- Featured Badge -->
        <div v-if="project.featured" class="absolute top-4 right-4 bg-yellow-500/90 text-white dark:text-yellow-100 text-xs font-bold px-3 py-1 rounded-full backdrop-blur-sm shadow-sm">
            Featured
        </div>
    </div>

    <!-- Content -->
    <div class="p-6 flex flex-col flex-1">
        <h3 class="text-xl font-bold text-gray-900 dark:text-white mb-3 group-hover:text-cyan-600 dark:group-hover:text-cyan-400 transition-colors">
            {{ project.title }}
        </h3>
        
        <p class="text-gray-600 dark:text-gray-400 text-sm leading-relaxed mb-6 flex-1 line-clamp-4">
            {{ project.description }}
        </p>
        
        <!-- Tech Stack Tags -->
        <div class="flex flex-wrap gap-2 mt-auto">
            <span 
                v-for="(tag, index) in project.tags" 
                :key="index"
                class="text-xs font-medium px-2.5 py-1 rounded bg-gray-100 dark:bg-white/5 text-gray-700 dark:text-gray-300 border border-gray-200 dark:border-white/10"
            >
                {{ tag }}
            </span>
        </div>
    </div>
  </div>
</template>
