<script setup>
import { X, ExternalLink, Github, LockKeyhole } from 'lucide-vue-next'
defineProps({
    project: Object,
    isOpen: Boolean
})
defineEmits(['close'])
</script>

<template>
  <div v-if="isOpen" class="fixed inset-0 z-[100] flex items-center justify-center p-4 sm:p-6" @click.self="$emit('close')">
    <div class="fixed inset-0 bg-black/60 backdrop-blur-sm transition-opacity" @click="$emit('close')"></div>
    
    <div class="relative bg-white dark:bg-[#0D1117] border border-gray-200 dark:border-gray-800 rounded-2xl shadow-2xl w-full max-w-4xl max-h-[90vh] overflow-y-auto flex flex-col transform transition-all z-10 animate-fade-in-up">
        <!-- Close Button -->
        <button @click="$emit('close')" class="absolute top-4 right-4 p-2 bg-gray-100 dark:bg-black/30 hover:bg-gray-200 dark:hover:bg-black/50 rounded-full text-gray-600 dark:text-gray-300 transition-colors z-20">
            <X class="w-5 h-5"/>
        </button>

        <!-- Image -->
        <div class="w-full sm:h-80 bg-gray-900 dark:bg-[#0D1117] relative flex items-center justify-center overflow-hidden">
            <img v-if="project?.image" :src="project.image" class="w-full h-full object-contain" :alt="project?.title" />
            <div v-else class="w-full h-full flex items-center justify-center text-gray-400 dark:text-gray-500">
                <span class="text-sm">Image Placeholder</span>
            </div>
        </div>

        <!-- Details -->
        <div class="p-6 md:p-10">
            <h2 class="text-3xl font-extrabold text-gray-900 dark:text-white mb-4">{{ project?.title }}</h2>
            
            <div class="flex flex-wrap gap-2 mb-6">
                 <span v-for="(tag, index) in project?.tags" :key="index" class="text-xs font-semibold px-3 py-1 rounded-full bg-cyan-500/10 text-cyan-700 dark:text-cyan-400 border border-cyan-500/20">
                    {{ tag }}
                </span>
            </div>

            <p class="text-gray-600 dark:text-gray-300 text-lg leading-relaxed mb-8">
                {{ project?.description }}
            </p>

            <!-- Links -->
            <div class="flex flex-wrap gap-4 items-center">
                <!-- Live link if public -->
                <a
                    v-if="project?.isPublic && project?.liveUrl"
                    :href="project.liveUrl"
                    target="_blank"
                    rel="noopener noreferrer"
                    class="flex items-center gap-2 px-6 py-3 bg-cyan-600 dark:bg-cyan-500 hover:bg-cyan-700 dark:hover:bg-cyan-400 text-white dark:text-black font-semibold rounded-lg transition-colors"
                >
                    <ExternalLink class="w-4 h-4" /> Live Demo
                </a>
                <!-- Not accessible notice -->
                <span
                    v-else-if="project?.isPublic === false"
                    class="flex items-center gap-2 px-6 py-3 bg-gray-100 dark:bg-white/5 text-gray-500 dark:text-gray-400 font-semibold rounded-lg border border-gray-200 dark:border-white/10 cursor-default"
                >
                    <LockKeyhole class="w-4 h-4" /> Not Publicly Accessible
                </span>
                <!-- GitHub -->
                <a v-if="project?.githubUrl" :href="project.githubUrl" target="_blank" rel="noopener noreferrer" class="flex items-center gap-2 px-6 py-3 bg-gray-100 dark:bg-white/10 hover:bg-gray-200 dark:hover:bg-white/20 text-gray-900 dark:text-white font-semibold rounded-lg transition-colors border border-transparent dark:border-white/10">
                    <Github class="w-4 h-4" /> View Code
                </a>
            </div>
        </div>
    </div>
  </div>
</template>

<style scoped>
@keyframes fade-in-up {
  0% {
    opacity: 0;
    transform: translateY(20px) scale(0.95);
  }
  100% {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}
.animate-fade-in-up {
  animation: fade-in-up 0.3s ease-out forwards;
}
</style>
