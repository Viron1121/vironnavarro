<script setup>
import ProcessCard from '../ui/ProcessCard.vue'
import { Map, Code2, TestTube, ShieldCheck, Rocket, Wrench } from "lucide-vue-next"

const processes = [
  {
    title: "Planning & Architecture",
    description: "Requirements analysis, system design, technical specifications, and architectural decision records.",
    badge: "Week 1-2",
    icon: Map
  },
  {
    title: "Development",
    description: "Test-driven development, code reviews, pair programming, and continuous integration.",
    badge: "Week 2-6",
    icon: Code2
  },
  {
    title: "Testing & QA",
    description: "Unit tests, integration tests, E2E testing, performance testing, and security audits.",
    badge: "Continuous",
    icon: TestTube
  },
  {
    title: "Security & Compliance",
    description: "Security scanning, vulnerability assessment, compliance checks, and penetration testing.",
    badge: "Week 5-6",
    icon: ShieldCheck
  },
   {
    title: "Deployment",
    description: "Continuous deployment, rolling updates, and rollback procedures.",
    badge: "Week 6",
    icon: Rocket
  },
   {
    title: "Maintenance & Support",
    description: "On-call support, incident management, and ongoing maintenance.",
    badge: "Continuous",
    icon: Wrench
  }
]
</script>

<template>
<section class="bg-gray-50 dark:bg-[#0B0E14] text-gray-900 dark:text-white py-24 transition-colors duration-300" id="Process-Timeline">
  <div class="max-w-7xl mx-auto px-6">
    
    <span class="text-cyan-600 dark:text-cyan-400 text-sm tracking-widest uppercase">Development Pipeline</span>
    <h2 class="mt-4 text-4xl md:text-5xl font-extrabold">Process That Works.</h2>
    <p class="mt-2 max-w-3xl text-gray-600 dark:text-gray-400">Proven engineering workflow that delivers quality, on time, every time.</p>

    <div class="mt-16 max-w-4xl">
      <!-- Relative container for timeline vertical line -->
      <div class="relative border-l-2 border-cyan-900/40 dark:border-cyan-900/60 ml-6">
        <ProcessCard 
          v-for="(process, idx) in processes" 
          :key="idx"
          class="-ml-6"
          :title="process.title"
          :description="process.description"
          :badge="process.badge"
          :icon="process.icon"
        />
      </div>
    </div>

  </div>
</section>
</template>