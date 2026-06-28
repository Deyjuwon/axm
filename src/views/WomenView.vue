<script setup>
import ProductGrid from '@/components/ProductGrid.vue'
import { ref, onMounted } from 'vue' 

const womenProducts = ref([])

onMounted(async () => {
  const response = await fetch('http://localhost:3000/products')
  const data = await response.json()
  womenProducts.value = data.filter(product => product.category === 'women')

})
</script>

<template>
  <ProductGrid
    :products="womenProducts"
    title="Women Collection"
    tag="#women"
    :showViewAll=false
  />
</template>