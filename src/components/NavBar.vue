<script setup>
import logo from '@/assets/logo.png';
import { RouterLink, useRoute } from 'vue-router';

const route = useRoute();

const isActive = (path) => route.path === path;
</script>

<template>
  <nav class="grid font-orbitron grid-cols-3 items-center px-10 h-16 bg-[#F5F5F7] text-[14px] font-medium">

    <div class="flex items-center gap-6 h-full">

      <RouterLink to="/newarrivals" class="relative hover:opacity-60 transition">
        New Arrivals
        <span 
          v-if="isActive('/newarrivals')"
          class="absolute left-1/2 -translate-x-1/2 -bottom-1 w-1/2 h-2px bg-black"
        ></span>
      </RouterLink>

      <RouterLink to="/men" class="relative hover:opacity-60 transition">
        Men
        <span 
          v-if="isActive('/men')"
          class="absolute left-1/2 -translate-x-1/2 -bottom-1 w-1/2 h-2px bg-black"
        ></span>
      </RouterLink>

      <RouterLink to="/women" class="relative hover:opacity-60 transition">
        Women
        <span 
          v-if="isActive('/women')"
          class="absolute left-1/2 -translate-x-1/2 -bottom-1 w-1/2 h-2px bg-black"
        ></span>
      </RouterLink>

      <RouterLink to="/contact" class="relative hover:opacity-60 transition">
        Contact Us
        <span 
          v-if="isActive('/contact')"
          class="absolute left-1/2 -translate-x-1/2 -bottom-1 w-1/2 h-2px bg-black"
        ></span>
      </RouterLink>

    </div>

 
    <div class="flex justify-center items-center h-full">
      <RouterLink to="/">
        <img 
          :src="logo" 
          alt="Axm Logo" 
          class="h-20 md:h-12 object-contain"
        />
      </RouterLink>
    </div>

 
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