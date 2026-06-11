<script setup>
import ProductGrid from '@/components/ProductGrid.vue'
import { products } from '@/data/products'

const womenProducts = products.filter(
  product => product.category === 'women'
)
</script>

<template>
  <ProductGrid
    :products="womenProducts"
    title="Women Collection"
    tag="#women"
    :showViewAll=false
  />
</template>