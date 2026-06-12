<script setup>
import { RouterLink } from 'vue-router';
defineProps({
  products: {
    type: Array,
    required: true
  },

  title: {
    type: String,
    default: 'Products'
  },

  tag: {
    type: String,
    default: '#products'
  },

  showViewAll: {
    type: Boolean,
    default: true
  }
})
</script>

<template>
  <section class="px-6 md:px-12 py-12">

    <!-- Header -->
    <div class="flex items-center justify-between mb-8">

      <div>
        <p class="text-xs text-gray-400 tracking-widest uppercase mb-1">
          {{ tag }}
        </p>

        <h2 class="text-2xl md:text-3xl font-bold text-gray-900">
          {{ title }}
        </h2>
      </div>

      <RouterLink
        v-if="showViewAll"
        to="/newarrivals"
        class="text-sm border border-gray-300 rounded-full px-4 py-1.5 text-gray-600 hover:bg-gray-50 transition"
      >
        View all
    </RouterLink>

    </div>

    <!-- Grid -->
    <div class="grid grid-cols-2 md:grid-cols-4 gap-4 md:gap-6">

      <div
        v-for="product in products"
        :key="product.id"
        class="group cursor-pointer"
      >

        <!-- Image -->
        <div class="overflow-hidden rounded-lg bg-gray-100 w-full aspect-[3/4]">
          <img
            :src="product.images[0]"
            :alt="product.name"
            class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500"
          />
        </div>

        <!-- Info -->
        <div class="mt-3">
          <p class="text-sm md:text-base font-medium text-gray-900">
            {{ product.name }}
          </p>
          <p class="text-sm text-gray-500 mt-0.5">
            {{ product.price }}
          </p>
        </div>

      </div>

    </div>

  </section>
</template>