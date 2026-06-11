<script setup>
import ProductGrid from '@/components/ProductGrid.vue'


</script>

<template>
  <ProductGrid
    :products="womenProducts"
    title="Women Collection"
    tag="#women"
  />
</template>