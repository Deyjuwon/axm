<script setup>
import ProductGrid from '@/components/ProductGrid.vue'

import pro1 from '@/assets/pro1.svg'
import pro2 from '@/assets/pro2.svg'
import pro3 from '@/assets/pro3.svg'
import pro4 from '@/assets/pro4.svg'

const menProducts = [
  { id: 1, name: 'Male Aso Oke', price: '₦100,000', img: pro1 },
  { id: 2, name: 'Esu Pants', price: '₦100,000', img: pro2 },
  { id: 3, name: 'Male Aso Oke Jacket', price: '₦100,000', img: pro3 },
  { id: 4, name: 'Female Aso Oke', price: '₦100,000', img: pro4 },
]
</script>

<template>
  <ProductGrid
    :products="menProducts"
    title="Men Collection"
    tag="#menswear"
    :showViewAll=false
  />
</template>