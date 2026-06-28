<script setup>
import ProductGrid from '@/components/ProductGrid.vue'
import { ref, onMounted } from 'vue'


const newArrivals = ref([])

onMounted(async () => {
  const response = await fetch('http://localhost:3000/products')
  const data = await response.json()
  newArrivals.value = data.filter(product => product.new_arrival)
})

</script>

<template>
  <ProductGrid
    :products="newArrivals"
    title="New Arrivals"
    tag="#newcollection"
    :showViewAll=false
  />
</template>