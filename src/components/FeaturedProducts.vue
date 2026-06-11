<script setup>
import ProductGrid from './ProductGrid.vue'
import { products } from '@/data/products'

const featuredProducts = products.filter(
  product => product.featured
)
</script>

<template>
  <ProductGrid
    :products="featuredProducts"
    title="Featured Products"
    tag="#bestseller"
  />
</template>