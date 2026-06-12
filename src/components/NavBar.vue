<script setup>
import { ref } from 'vue';
import logo from '@/assets/logo.png';
import { RouterLink } from 'vue-router';

const mobileMenuOpen = ref(false);
</script>

<template>
  <nav class="bg-[#F5F5F7] border-b border-gray-200">
    
    <!-- Desktop -->
    <div class="hidden md:grid grid-cols-3 items-center px-10 h-16 text-[14px] font-medium">
      <!-- Left -->
      <div class="flex items-center gap-6">
        <RouterLink to="/newarrivals">New Arrivals</RouterLink>
        <RouterLink to="/men">Men</RouterLink>
        <RouterLink to="/women">Women</RouterLink>
        <RouterLink to="/contact">Contact Us</RouterLink>
      </div>

      <!-- Center -->
      <div class="flex justify-center">
        <RouterLink to="/">
          <img :src="logo" alt="AXM" class="h-12" />
        </RouterLink>
      </div>

      <!-- Right -->
      <div class="flex justify-end gap-4">
        <button><i class="pi pi-search"></i></button>
        <button><i class="pi pi-shopping-bag"></i></button>
      </div>
    </div>

    <!-- Mobile -->
    <div class="md:hidden h-16 flex items-center justify-between px-5">

      <!-- Hamburger -->
      <button @click="mobileMenuOpen = !mobileMenuOpen">
        <i class="pi pi-bars text-xl"></i>
      </button>

      <!-- Logo -->
      <RouterLink to="/">
        <img
          :src="logo"
          alt="AXM"
          class="h-10 object-contain"
        />
      </RouterLink>

      <!-- Icons -->
      <div class="flex items-center gap-4">
        <button>
          <i class="pi pi-user text-lg"></i>
        </button>

        <button class="relative">
          <i class="pi pi-shopping-bag text-lg"></i>

          <span
            class="absolute -top-2 -right-2 bg-black text-white text-[10px] rounded-full w-4 h-4 flex items-center justify-center"
          >
            2
          </span>
        </button>
      </div>
    </div>

    <!-- Mobile Drawer -->
    <transition name="fade">
      <div
        v-if="mobileMenuOpen"
        class="md:hidden border-t border-gray-200 bg-white"
      >
        <div class="flex flex-col py-4">
          <RouterLink
            to="/newarrivals"
            class="px-5 py-3 hover:bg-gray-50"
          >
            New Arrivals
          </RouterLink>

          <RouterLink
            to="/men"
            class="px-5 py-3 hover:bg-gray-50"
          >
            Men
          </RouterLink>

          <RouterLink
            to="/women"
            class="px-5 py-3 hover:bg-gray-50"
          >
            Women
          </RouterLink>

          <RouterLink
            to="/contact"
            class="px-5 py-3 hover:bg-gray-50"
          >
            Contact Us
          </RouterLink>
        </div>
      </div>
    </transition>

  </nav>
</template>