<script setup>
import { RouterLink } from 'vue-router';
</script>

<template>
  <section
    class="min-h-[calc(100vh-64px)] flex flex-col items-center justify-center text-center px-6"
  >
    <h1 class="text-8xl font-bold tracking-tight text-gray-900">404</h1>

    <h2 class="mt-4 text-2xl md:text-3xl font-semibold text-gray-900">
      Page not found
    </h2>

    <p class="mt-3 max-w-md text-gray-500">
      The page you're looking for may have been moved, removed, or never existed.
    </p>

    <div class="mt-8 flex gap-4">
      <RouterLink
        to="/"
        class="bg-black text-white px-6 py-3 rounded-full hover:opacity-90 transition"
      >
        Back Home
      </RouterLink>

      <RouterLink
        to="/newarrivals"
        class="border border-gray-300 px-6 py-3 rounded-full hover:bg-gray-100 transition"
      >
        Continue Shopping
      </RouterLink>
    </div>
  </section>
</template>