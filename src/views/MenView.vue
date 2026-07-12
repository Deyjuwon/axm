<script setup>
import ProductGrid from '@/components/ProductGrid.vue'
import { ref, onMounted } from 'vue'

const menProducts = ref([])
const API_BASE = import.meta.env.VITE_API_URL

onMounted(async () => {
  try {
    const response = await fetch(`${API_BASE}/products?category=Men`)

    if (!response.ok) {
      throw new Error('Failed to fetch men products')
    }

    menProducts.value = await response.json()
  } catch (error) {
    console.error(error)
  }
})
</script>

<template>
  <ProductGrid
    :products="menProducts"
    title="Men Collection"
    tag="#men"
    :showViewAll="false"
  />
</template>