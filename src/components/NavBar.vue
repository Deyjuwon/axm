<script setup>
import logo from '@/assets/logo.png';
import { RouterLink } from 'vue-router';
</script>

<template>
  <nav class="grid font-orbitron grid-cols-3 items-center px-10 h-16 bg-[#F5F5F7] text-[14px] font-medium">

    <!-- Left -->
    <div class="flex items-center gap-6 h-full">
      <RouterLink to="/newarrivals" class="hover:opacity-60 transition font-orbitron">
        New Arrivals
      </RouterLink>

      <RouterLink to="/men" class="hover:opacity-60 transition">
        Men
      </RouterLink>

      <RouterLink to="/women" class="hover:opacity-60 transition">
        Women
      </RouterLink>

      <RouterLink to="/contact" class="hover:opacity-60 transition">
        Contact Us
      </RouterLink>
    </div>

    <!-- Center Logo -->
    <div class="flex justify-center items-center h-full">
      <RouterLink to="/">
        <img 
          :src="logo" 
          alt="Axm Logo" 
          class="h-20 md:h-12 object-contain"
        />
      </RouterLink>
    </div>

    <!-- Right -->
    <div class="flex justify-end items-center gap-4 h-full">

      <button class="hover:opacity-60 transition">
        <span class="pi pi-search text-lg"></span>
      </button>

      <button class="hover:opacity-60 transition relative">
        <span class="pi pi-shopping-bag text-lg"></span>

      </button>

    </div>

  </nav>
</template>