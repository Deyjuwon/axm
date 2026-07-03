<script setup>
import { ref, onMounted } from 'vue'
import { useRoute } from 'vue-router'
import ProductGrid from '@/components/ProductGrid.vue'

const route = useRoute()

const product = ref(null)
const loading = ref(true)
const quantity = ref(1)
const relatedProducts = ref([])

const API_BASE = import.meta.env.VITE_API_URL


const imageUrl = (url) => {
  if (!url) return ''
  return url.startsWith('http') ? url : `${API_BASE}${url}`
}

const fetchProduct = async () => {
  try {
    loading.value = true
    const response = await fetch(`${API_BASE}/products/${route.params.id}`)
    product.value = response.ok ? await response.json() : null
  } catch (error) {
    console.error('Failed to fetch product:', error)
    product.value = null
  } finally {
    loading.value = false
  }
}

onMounted(fetchProduct)

const increaseQty = () => quantity.value++
const decreaseQty = () => {
  if (quantity.value > 1) quantity.value--
}
</script>

<template>
  <section class="px-6 md:px-12 py-12">

    <!-- Loading -->
    <div v-if="loading" class="text-center py-20">
      Loading product...
    </div>

    <!-- Product Not Found -->
    <div v-else-if="!product" class="text-center py-20">
      Product not found
    </div>

    <!-- Product Page -->
    <div v-else class="grid lg:grid-cols-2 lg:gap-20 gap-12">

      <!-- Image -->
      <div class="relative bg-[#f7f7f7] rounded-lg overflow-hidden aspect-[4/5]">
        <img
          :src="imageUrl(product.image_url)"
          :alt="product.name"
          class="w-full h-full object-cover"
        />
      </div>

      <!-- Info -->
      <div class="lg:sticky lg:top-24 h-fit">

        <h1 class="text-3xl font-semibold">
          {{ product.name }}
        </h1>

        <p class="text-2xl mt-4">
          ₦ {{ product.price }}
        </p>

        <p class="mt-6 text-gray-600">
          {{ product.description }}
        </p>

        <!-- Quantity -->
        <div class="mt-8">
          <h3 class="font-medium mb-3">Quantity</h3>
          <div class="flex items-center border w-fit">
            <button @click="decreaseQty" class="w-12 h-12">−</button>
            <span class="w-12 text-center">{{ quantity }}</span>
            <button @click="increaseQty" class="w-12 h-12">+</button>
          </div>
        </div>

        <button class="w-full mt-8 bg-black text-white py-4 rounded-md">
          Add To Cart
        </button>

      </div>

    </div>

    <!-- Related -->
    <div v-if="product" class="mt-24 -mx-6 md:-mx-12">
      <ProductGrid
        :products="relatedProducts"
        title="Related Products"
        tag="#related"
        :showViewAll="false"
      />
    </div>

  </section>
</template>
