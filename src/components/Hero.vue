<script setup>
import hero1 from '@/assets/hero1.jpg'
import hero2 from '@/assets/hero2.jpg'
</script>

<template>
  <section class="relative flex w-full h-[calc(100vh-64px)]" style="gap:0; font-size:0;">

    <img :src="hero1" alt="" class="w-full md:w-1/2 h-full object-cover block" />
    <img :src="hero2" alt="" class="hidden md:block w-1/2 h-full object-cover" />

    <!-- Gradient scrim -->
    <div class="absolute inset-0 bg-gradient-to-t from-black/70 via-black/20 to-transparent pointer-events-none" />

    <!-- Text overlay -->
    <div class="absolute inset-0 flex flex-col items-center justify-end pb-16 md:pb-20 px-4">
      <div class="text-center">

        <p class="text-white/70 text-xs tracking-[0.3em] uppercase mb-3 font-light">
          New Collection
        </p>

        <h1
          class="text-white font-bold text-4xl md:text-5xl lg:text-6xl leading-[1.1] tracking-widest uppercase mb-2"
          style="text-shadow: 0 2px 20px rgba(0,0,0,0.5);"
        >
          Rooted in Tradition,
        </h1>
        <h1
          class="text-white font-bold text-4xl md:text-5xl lg:text-6xl leading-[1.1] tracking-widest uppercase mb-8"
          style="text-shadow: 0 2px 20px rgba(0,0,0,0.5);"
        >
          Styled for the Future
        </h1>

        <button class="
          bg-white/10 backdrop-blur-sm
          text-white text-sm font-semibold
          px-8 md:px-10 py-3 rounded-full
          border border-white/40
          hover:bg-white hover:text-black
          transition-all duration-300 cursor-pointer
        ">
          Shop Now
        </button>

      </div>
    </div>

  </section>
</template>