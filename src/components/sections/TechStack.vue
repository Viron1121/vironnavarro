<template>
  <section class="bg-white dark:bg-[#121218] text-gray-900 dark:text-white py-24 transition-colors duration-300" id="Tech-Stack">
    <div class="max-w-7xl mx-auto px-6">
      <!-- Section header -->
      <span class="text-cyan-600 dark:text-cyan-400 text-sm tracking-widest uppercase">
        Tech Stack
      </span>

      <h2 class="mt-4 text-4xl md:text-5xl font-extrabold">
        Tools of the Trade.
      </h2>

      <p class="mt-6 max-w-3xl text-gray-600 dark:text-gray-400 text-lg">
        Technology is a means, not an end. I choose tools based on scalability,
        maintainability, and business requirements.
      </p>

      <!-- Grid -->
      <div class="mt-16 grid gap-8 md:grid-cols-2 lg:grid-cols-3">
        <TechCard title="Backend & APIs" :items="['Laravel', 'PHP', 'Python', 'MySQL']" />

        <TechCard title="Frontend" :items="['React', 'TypeScript', 'Vue.js']" />

        <TechCard title="Infrastructure" :items="['AWS', 'Supabase']" />

        <TechCard title="CI/CD & DevOps" :items="['GitLab CI/CD', 'Git']" />

        <TechCard
            title="System Administration"
            :items="[
                'Linux (Ubuntu)',
                'SSH Configuration',
                'User & Permission Management',
                'Nginx',
                'Process Management (systemd)',
                'Firewall (UFW)'
            ]"
        />

        <TechCard
          title="Tools & Workflow"
          :items="['Figma', 'Jira', 'Confluence', 'Slack', 'Postman']"
        />

        <TechCard
          title="Database"
          :items="['MySQL', 'PostgreSQL', 'MSSQL', 'Supabase', 'MongoDB', 'Redis']"
        />

        
        <TechCard
          title="AI Assistance"
          :items="['Gemini', 'ChatGPT', 'Cursor']"
        />


      </div>
    </div>
  </section>
</template>

<script setup>
import TechCard from '../ui/TechCard.vue'
</script>
