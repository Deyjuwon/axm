<script setup>
import { RouterLink } from 'vue-router';
</script>


<template>
  <footer class="rounded-t-4xl px-8 py-16 md:py-24 bg-[#252525] text-white">


    <div class="flex flex-col items-center text-center gap-4 max-w-2xl mx-auto">

      <h2 class="text-2xl md:text-4xl font-bold">
        Join The AxM Community!
      </h2>

      <p class="text-sm md:text-base text-white/80">
        Be the first to get the latest updates on our promotion campaigns, products and services.
      </p>

      <button class="flex items-center gap-2 border border-white/40 text-sm px-6 py-2.5 rounded-full hover:bg-white hover:text-[#695C5C] transition cursor-pointer">
        Sign up <span>→</span>
      </button>

    </div>


    <div class="my-10 border-t border-white/20"></div>


    <div class="flex flex-col md:flex-row items-center justify-between gap-4 text-xs text-white/70">

      <div class="flex gap-6">
        <a href="#" class="hover:text-white transition">About Us</a>
        <RouterLink to="/contact" class="hover:text-white transition">Contact Us</RouterLink>
        <a href="#" class="hover:text-white transition">FAQs</a>
      </div>

      <p class="text-white/60">
        © 2026 AxM. All rights reserved.
      </p>

    </div>

  </footer>
</template>