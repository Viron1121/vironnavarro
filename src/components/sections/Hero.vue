<template>
  <section class="relative min-h-screen flex items-center bg-gray-50 dark:bg-[#0B0E14] text-gray-900 dark:text-white overflow-hidden transition-colors duration-300 pt-20">
    <div class="absolute inset-0 bg-gradient-to-br from-cyan-500/5 dark:from-cyan-500/10 via-transparent to-transparent"></div>

    <div class="relative z-10 max-w-7xl mx-auto px-6 py-12 grid md:grid-cols-2 gap-12 items-center">
      <!-- Left Details -->
      <div>
        <span
          class="inline-block mb-6 px-4 py-2 text-xs tracking-widest uppercase rounded-full
                 border border-cyan-500/30 dark:border-cyan-400/40 text-cyan-600 dark:text-cyan-400 bg-cyan-500/10 dark:bg-cyan-400/10"
        >
          Systems Engineer | Web Developer
        </span>

        <h1 class="text-5xl md:text-7xl font-extrabold leading-tight max-w-4xl">
          I build <span class="text-cyan-600 dark:text-cyan-400">SYSTEMS</span><br />
          that scale<br />
          businesses.
        </h1>

        <p class="mt-6 max-w-2xl text-gray-600 dark:text-gray-400 text-lg">
          Engineering reliable, scalable architectures for enterprise applications.
          From concept to deployment, I design systems that solve real business problems.
        </p>

        <div class="mt-10 flex gap-4">
          <a
            href="#Contact"
            class="px-6 py-3 rounded-lg bg-cyan-600 dark:bg-cyan-500 text-white dark:text-black font-semibold
                   hover:bg-cyan-700 dark:hover:bg-cyan-400 transition inline-block text-center"
          >
            Let’s Talk →
          </a>

          <a
            href="/cv_navarro.pdf"
            target="_blank"
            rel="noopener noreferrer"
            class="px-6 py-3 rounded-lg border border-gray-300 dark:border-white/20 text-gray-700 dark:text-white
                   hover:bg-gray-100 dark:hover:bg-white/10 transition inline-block text-center"
          >
            View CV
          </a>
        </div>
      </div>
      
      <!-- Right Image -->
      <div class="flex justify-center md:justify-end mt-12 md:mt-0">
        <div class="relative w-72 h-72 md:w-96 md:h-96 group">
          <!-- Glow Effect container -->
          <div class="absolute inset-0 bg-cyan-500 rounded-full blur-[80px] opacity-20 group-hover:opacity-40 transition-opacity duration-500"></div>
          
          <!-- Image -->
          <img 
            src="/profile.jpg" 
            alt="My Profile Picture" 
            class="relative w-full h-full object-cover rounded-full border border-gray-200 dark:border-white/10 shadow-2xl z-10 
                   group-hover:scale-[1.02] transition-transform duration-500" 
          />
        </div>
      </div>
      
    </div>
  </section>
</template>
