<script setup>
import ProductGrid from '@/components/ProductGrid.vue'
import { ref, onMounted } from 'vue'

const womenProducts = ref([])
const API_BASE = import.meta.env.VITE_API_URL

onMounted(async () => {
  try {
    const response = await fetch(`${API_BASE}/products?category=Women`)

    if (!response.ok) {
      throw new Error('Failed to fetch women products')
    }

    womenProducts.value = await response.json()
  } catch (error) {
    console.error(error)
  }
})
</script>

<template>
  <ProductGrid
    :products="womenProducts"
    title="Women Collection"
    tag="#men"
    :showViewAll="false"
  />
</template>