<script setup>
import ProductGrid from '@/components/ProductGrid.vue'
import { products } from '@/data/products'

const newArrivals = products.filter(
  product => product.newArrival
)
</script>

<template>
  <ProductGrid
    :products="newArrivals"
    title="New Arrivals"
    tag="#newcollection"
    :showViewAll=false
  />
</template>