<script setup>
    import ExperienceCard from '../ui/ExperienceCard.vue'

    const experiences = [
    {
        company: "Freelance",
        role: "Web Developer",
        year: "09/2025 - Present",
        location: "Remote",
        techStack: ["Laravel", "React", "MySQL", "Tailwind"],
        achievements: [
            "Develop and maintain web applications for clients",
            "Estimate project scope and deliver feature implementations based on client requirements.",
            "Create mockups and prototypes to visualize design concepts and gather feedback.",
            "Implement new features, bug fixes, and performance improvements."
        ]
    },
    {
        company: "Rarejob Philippines Inc.",
        role: "Systems Engineer",
        year: "02/2025 - 09/2025",
        location: "Remote",
        techStack: ["Laravel", "Vue", "Yii", "MySQL", "Gitlab CI/CD", "Figma", "AWS", "Jira", "Confluence", "Postman"],
        achievements: [
            "Part of the Website Support Team, ensuring system stability and supporting internal/external applications. ",
            "Assist in designing, troubleshooting, and deploying solutions that align with project requirements. ",
            "Implemented authentication and role based systems",
            "Optimized database queries for better performance",
            "Participating in code reviews, knowledge sharing sessions, and continuous learning initiatives to enhance team capabilities and project outcomes.",
            "Estimating project timelines and resources to ensure timely delivery. ",
        ]
    },
    {
        company: "National Center for Mental Health",
        role: "Full Stack Developer",
        year: "09/2023 - 12/2024",
        location: "Onsite",
        techStack: ["Laravel", "React Typescript", "MySQL", "Gitlab CI/CD", "Figma", "Postman"],
        achievements: [
            "Part of the Development Team for the Mental Health Information System (MHIS), a comprehensive web application designed to streamline mental health data management and enhance service delivery.",
            "Integrate different systems by developing APIs for seamless data exchange and enhanced functionality. I troubleshot and fixed system issues to ensure everything ran smoothly. ",
            "Communicate with stakeholders to gather requirements, share technical insights, and provide updates on system development and operational issues",
            "Developed and maintain the website's front-end using Blade, React, and TypeScript to create a smooth user experience. ",
            "Work on building and improving backend systems with PHP and the Laravel framework, handling business logic, databases, and server-side processes. "
        ]
    }
    ]
</script>

<template>
    <section class="bg-gray-50 dark:bg-[#0B0E14] text-gray-900 dark:text-white py-24 transition-colors duration-300" id="experience">

        <div class="max-w-7xl mx-auto px-6">

            <span class="text-cyan-600 dark:text-cyan-400 text-sm tracking-widest uppercase">
                Career Trajectory
            </span>

            <h2 class="mt-4 text-4xl md:text-5xl font-extrabold">
                Experience
            </h2>

            <div class="mt-16 space-y-10">

                <ExperienceCard
                    v-for="exp in experiences"
                    :key="exp.company"
                    :company="exp.company"
                    :role="exp.role"
                    :year="exp.year"
                    :location="exp.location"
                    :techStack="exp.techStack"
                    :achievements="exp.achievements"
                />

            </div>

        </div>

    </section>
</template>