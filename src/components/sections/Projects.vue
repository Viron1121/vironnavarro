<script setup>
import { ref, computed } from 'vue'
import ProjectCard from '../ui/ProjectCard.vue'
import ProjectModal from '../ui/ProjectModal.vue'

// Basic categories matching the screenshot
const categories = ['All Projects', 'Vue.js', 'Laravel', 'Full-Stack', 'React']
const activeCategory = ref('All Projects')

// Modal State
const isModalOpen = ref(false)
const selectedProject = ref(null)

const openModal = (project) => {
    selectedProject.value = project
    isModalOpen.value = true
    document.body.style.overflow = 'hidden' // Prevent bg scrolling
}

const closeModal = () => {
    isModalOpen.value = false
    selectedProject.value = null
    document.body.style.overflow = '' // Restore scrolling
}

// Sample project data reflecting the screenshot layout structure
const projects = [
    {
        id: 1,
        title: "Rarejob - Online English School",
        description: "Maintain and add feature patches for the Rarejob platform ensuring 100% system uptime by resolving 50+ technical tickets per month.",
        image: "/rarejob.png", 
        featured: true,
        category: "Full-Stack", 
        tags: ["Laravel", "Yii", "Vue.js", "TypeScript", "Full-Stack"]
    },
    {
        id: 2,
        title: "Curemed - Pharmacy Information System",
        description: "Built a information system for medicine of the hospital to track the medicine inventory and sales. featuring a dashboard for the admin to track the sales and inventory. It also features a patient management system to track the patient information and medical history. ensuring 100% system uptime by resolving 80+ technical tickets per month.",
        image: "/curemed.png",
        featured: true,
        category: "Full-Stack",
        tags: ["Laravel", "React", "PHP", "Responsive Design", "Figma"]
    },
    {
        id: 3,
        title: "MMS - Inventory Management System",
        description: "Maintain and add feature patches for the MMS platform ensuring 100% system uptime by resolving 30+ technical tickets per month.",
        image: "/mms.png",
        featured: true,
        category: "Full-Stack",
        tags: ["Laravel", "blade", "MySQL", "Figma", "Responsive Design"]
    },
]

// Filter logic
const filteredProjects = computed(() => {
    if (activeCategory.value === 'All Projects') {
        return projects
    }
    return projects.filter(project => 
        project.category === activeCategory.value || 
        project.tags.includes(activeCategory.value)
    )
})
</script>

<template>
  <section class="bg-white dark:bg-[#121218] text-gray-900 dark:text-white py-24 transition-colors duration-300" id="projects">
    <div class="max-w-7xl mx-auto px-6">
      
      <!-- Header -->
      <div class="text-center md:text-left mb-16">
        <span class="text-cyan-600 dark:text-cyan-400 text-sm tracking-widest uppercase mb-4 block">
            Portfolio
        </span>
        <h2 class="text-4xl md:text-5xl font-extrabold mb-8">
            Featured <span class="text-cyan-600 dark:text-cyan-400">Projects.</span>
        </h2>
        
        <!-- Filter Tabs -->
        <div class="flex flex-wrap justify-center md:justify-start gap-3">
            <button 
                v-for="cat in categories" 
                :key="cat"
                @click="activeCategory = cat"
                :class="[
                    'px-5 py-2.5 rounded-lg text-sm font-medium transition-all duration-300',
                    activeCategory === cat 
                        ? 'bg-cyan-600 text-white shadow-lg shadow-cyan-500/30 dark:shadow-cyan-400/20 ring-2 ring-cyan-500/50' 
                        : 'bg-gray-100 dark:bg-[#161B22] text-gray-600 dark:text-gray-300 hover:bg-gray-200 dark:hover:bg-[#1C2128] border border-transparent dark:border-gray-800'
                ]"
            >
                {{ cat }}
            </button>
        </div>
      </div>

      <!-- Projects Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <template v-if="filteredProjects.length">
            <ProjectCard 
                v-for="project in filteredProjects" 
                :key="project.id" 
                :project="project"
                @click="openModal"
            />
        </template>
        <div v-else class="col-span-full py-20 text-center text-gray-500 dark:text-gray-400">
            No projects found for this category.
        </div>
      </div>

    </div>

    <!-- Teleport Modal -->
    <Teleport to="body">
        <ProjectModal 
            :is-open="isModalOpen" 
            :project="selectedProject" 
            @close="closeModal" 
        />
    </Teleport>
  </section>
</template>
