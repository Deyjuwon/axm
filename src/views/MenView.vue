<script setup>
import ProductGrid from '@/components/ProductGrid.vue'
import { products } from '@/data/products'

const menProducts = products.filter(
  product => product.category === 'men'
)
</script>

<template>
  <ProductGrid
    :products="menProducts"
    title="Men Collection"
    tag="#men"
    :showViewAll=false
  />
</template>