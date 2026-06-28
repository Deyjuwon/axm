<script setup>
import ProductGrid from './ProductGrid.vue'
import { ref, onMounted } from 'vue'

const featuredProducts = ref([])

onMounted(async () => {
  try {
    const response = await fetch('http://localhost:3000/products')

    if (!response.ok) {
      throw new Error('Failed to fetch products')
    }

    const data = await response.json()

    featuredProducts.value = data.slice(0, 12)
  } catch (error) {
    console.error(error)
  }
})
</script>

<template>
  <ProductGrid
    :products="featuredProducts"
    title="Featured Products"
    tag="#bestseller"
  />
</template>