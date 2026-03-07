<template>
  <Navbar />
  <Hero />
  <About />
  <Techstack />
  <Experience />
  <ProcessTimeline />
  <ContactSection />
  <Footer />
</template>

<script setup>
    import Navbar from '../components/layout/Navbar.vue'
    import Hero from '../components/sections/Hero.vue'
    import About from '../components/sections/About.vue'
    import Techstack from '../components/sections/TechStack.vue'
    import Experience from '../components/sections/Experience.vue'
    import ProcessTimeline from '../components/sections/ProcessTimeline.vue'
    import ContactSection from '../components/sections/ContactSection.vue'
    import Footer from '../components/layout/Footer.vue'
</script>
