<script setup>
import { ref, computed, watch, onMounted } from 'vue'
import { useRoute } from 'vue-router'
import ProductGrid from '@/components/ProductGrid.vue'

const route = useRoute()

const product = ref(null)
const loading = ref(true)

const selectedImage = ref('')
const selectedSize = ref('')
const quantity = ref(1)
const currentIndex = ref(0)

// FETCH FROM RAILS API
const fetchProduct = async () => {
  try {
    loading.value = true

    const response = await fetch(
      `http://localhost:3000/products/${route.params.id}`
    )

    if (!response.ok) {
      product.value = null
      return
    }

    const data = await response.json()

  
    product.value = {
      ...data,
      images: data.images || [data.image_url],
      sizes: data.sizes || [] 
    }

  } catch (error) {
    console.error('Failed to fetch product:', error)
    product.value = null
  } finally {
    loading.value = false
  }
}

onMounted(fetchProduct)


watch(product, (newProduct) => {
  if (!newProduct) return

  currentIndex.value = 0
  selectedImage.value = newProduct.images?.[0] || ''
  quantity.value = 1

  if (newProduct.sizes?.length) {
    selectedSize.value = newProduct.sizes[0]
  }
})


const setImageByIndex = (index, images) => {
  if (!images?.length) return
  currentIndex.value = index
  selectedImage.value = images[index]
}

const nextImage = () => {
  if (!product.value?.images?.length) return
  const images = product.value.images
  const next = (currentIndex.value + 1) % images.length
  setImageByIndex(next, images)
}

const prevImage = () => {
  if (!product.value?.images?.length) return
  const images = product.value.images
  const prev =
    (currentIndex.value - 1 + images.length) % images.length
  setImageByIndex(prev, images)
}

// QUANTITY
const increaseQty = () => quantity.value++
const decreaseQty = () => {
  if (quantity.value > 1) quantity.value--
}


const relatedProducts = ref([])
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

      <!-- Images -->
      <div>

        <div class="relative bg-[#f7f7f7] rounded-lg overflow-hidden aspect-[4/5] group">

          <img
            :src="selectedImage"
            :alt="product.name"
            class="w-full h-full object-cover"
          />

          <button @click="prevImage"
            class="absolute left-3 top-1/2 -translate-y-1/2 bg-black/30 text-white w-10 h-10 rounded-full opacity-0 group-hover:opacity-100">
            ‹
          </button>

          <button @click="nextImage"
            class="absolute right-3 top-1/2 -translate-y-1/2 bg-black/30 text-white w-10 h-10 rounded-full opacity-0 group-hover:opacity-100">
            ›
          </button>

        </div>

        <!-- Thumbnails -->
        <div v-if="product.images?.length > 1" class="flex gap-3 mt-5 overflow-x-auto">

          <button
            v-for="(image, index) in product.images"
            :key="index"
            @click="setImageByIndex(index, product.images)"
            class="w-20 h-20 border rounded-md overflow-hidden"
            :class="selectedImage === image ? 'border-black' : 'border-gray-200'"
          >
            <img :src="image" class="w-full h-full object-cover" />
          </button>

        </div>

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