<script setup>
import ProductGrid from '@/components/ProductGrid.vue'
import { ref, onMounted } from 'vue'

const menProducts = ref([])

onMounted(async () => {
  const response = await fetch('http://localhost:3000/api/v1/products')
  const data = await response.json()
  menProducts.value = data.filter(product => product.category === 'men')
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