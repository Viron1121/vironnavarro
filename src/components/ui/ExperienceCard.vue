<template>
    <div class="border border-gray-200 dark:border-gray-800 rounded-xl p-8 bg-white dark:bg-[#0D1117] hover:border-cyan-500 transition duration-300">
        
       <div class="flex items-center gap-4 mb-6">
            <!-- Building Icon -->
            <div class="w-10 h-10 flex items-center justify-center bg-gray-50 dark:bg-[#111827] border border-gray-200 dark:border-gray-700 rounded-lg">
                <svg xmlns="http://www.w3.org/2000/svg" 
                     class="w-5 h-5 text-cyan-600 dark:text-cyan-400"
                     fill="none" 
                     viewBox="0 0 24 24" 
                     stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                        d="M3 21h18M5 21V7a2 2 0 012-2h3V3h4v2h3a2 2 0 012 2v14M9 9h.01M9 12h.01M9 15h.01M15 9h.01M15 12h.01M15 15h.01"/>
                </svg>
            </div>

            <hr class="flex-1 border-gray-200 dark:border-gray-700" />
        </div>

        <!-- Title -->
        <h3 class="text-2xl font-semibold">
            {{ company }}
        </h3>

        <p class="text-cyan-600 dark:text-cyan-400 mt-1">
            {{ role }}
        </p>

        <!-- Meta -->
        <div class="flex gap-6 text-gray-500 dark:text-gray-400 text-sm mt-3">
            <span>📅 {{ year }}</span>
            <span>📍 {{ location }}</span>
        </div>

        <!-- Tech Stack -->
        <div class="flex flex-wrap gap-2 mt-6">
            <span
                v-for="tech in techStack"
                :key="tech"
                class="px-3 py-1 text-sm bg-gray-50 dark:bg-[#111827] border border-gray-200 dark:border-gray-700 rounded-full text-gray-700 dark:text-white"
            >
                {{ tech }}
            </span>
        </div>

        <!-- Achievements -->
        <ul class="mt-6 space-y-4 text-gray-600 dark:text-gray-300">
            <li
                v-for="item in achievements"
                :key="item"
                class="flex gap-3"
            >
                <span class="text-cyan-600 dark:text-cyan-400">•</span>
                {{ item }}
            </li>
        </ul>

    </div>
</template>

<script setup>
defineProps({
    company: String,
    role: String,
    year: String,
    location: String,
    techStack: Array,
    achievements: Array
})
</script>