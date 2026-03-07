<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { ArrowUp, ArrowDown } from 'lucide-vue-next'

const showControls = ref(false)

const handleScroll = () => {
    // Show buttons when scrolled down 300px
    showControls.value = window.scrollY > 300
}

const scrollToTop = () => {
    window.scrollTo({
        top: 0,
        behavior: 'smooth'
    })
}

const scrollToBottom = () => {
    window.scrollTo({
        top: document.documentElement.scrollHeight,
        behavior: 'smooth'
    })
}

onMounted(() => {
    window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
    <div
        class="fixed right-6 bottom-6 flex flex-col gap-3 z-50 transition-all duration-300"
        :class="showControls ? 'opacity-100 translate-y-0 visible' : 'opacity-0 translate-y-4 invisible'"
    >
        <!-- Scroll to Top Button -->
        <button
            @click="scrollToTop"
            class="p-3 bg-cyan-600 dark:bg-cyan-500 text-white dark:text-black rounded-full shadow-lg hover:bg-cyan-700 dark:hover:bg-cyan-400 hover:scale-110 transition-all duration-300 group"
            title="Scroll to Top"
        >
            <ArrowUp class="w-5 h-5" stroke-width="2.5" />
        </button>

        <!-- Scroll to Bottom Button -->
        <button
            @click="scrollToBottom"
            class="p-3 bg-white dark:bg-[#0D1117] text-gray-700 dark:text-gray-300 border border-gray-200 dark:border-gray-800 rounded-full shadow-lg hover:text-cyan-600 dark:hover:text-cyan-400 hover:border-cyan-500/30 dark:hover:border-cyan-500/30 hover:scale-110 transition-all duration-300"
            title="Scroll to Bottom"
        >
            <ArrowDown class="w-5 h-5" stroke-width="2.5" />
        </button>
    </div>
</template>
