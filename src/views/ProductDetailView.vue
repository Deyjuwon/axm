<script setup>
import { computed, ref, watch } from 'vue'
import { useRoute } from 'vue-router'
import ProductGrid from '@/components/ProductGrid.vue'
import { products } from '@/data/products'

const route = useRoute()

const product = computed(() =>
  products.find(p => p.id === Number(route.params.id))
)

const selectedImage = ref('')
const selectedSize = ref('')
const quantity = ref(1)

const currentIndex = ref(0)

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

watch(
  product,
  (newProduct) => {
    if (newProduct) {
      currentIndex.value = 0
      selectedImage.value = newProduct.images[0]
      quantity.value = 1

      if (newProduct.sizes?.length) {
        selectedSize.value = newProduct.sizes[0]
      }
    }
  },
  { immediate: true }
)

const increaseQty = () => quantity.value++

const decreaseQty = () => {
  if (quantity.value > 1) quantity.value--
}

const relatedProducts = computed(() => {
  if (!product.value) return []

  return products
    .filter(
      p =>
        p.category === product.value.category &&
        p.id !== product.value.id
    )
    .slice(0, 4)
})
</script>

<template>
  <section
    v-if="product"
    class=" px-6 md:px-12 py-12"
  >
    <div class="grid lg:grid-cols-2 lg:gap-20 gap-12">

      <!-- Product Images -->
      <div>

        <!-- Main Image -->
        <div class="relative bg-[#f7f7f7] rounded-lg overflow-hidden aspect-[4/5] group">

          <img
            :src="selectedImage"
            :alt="product.name"
            class="w-full h-full object-cover"
          />

          <!-- Left Arrow -->
          <button
            @click="prevImage"
            class="absolute left-3 top-1/2 -translate-y-1/2 bg-black/30 hover:bg-black/50 text-white w-10 h-10 rounded-full flex items-center justify-center opacity-0 group-hover:opacity-100 transition"
          >
            ‹
          </button>

          <!-- Right Arrow -->
          <button
            @click="nextImage"
            class="absolute right-3 top-1/2 -translate-y-1/2 bg-black/30 hover:bg-black/50 text-white w-10 h-10 rounded-full flex items-center justify-center opacity-0 group-hover:opacity-100 transition"
          >
            ›
          </button>

        </div>

        <!-- Thumbnails -->
        <div
          v-if="product.images.length > 1"
          class="flex gap-3 mt-5 overflow-x-auto"
        >
          <button
            v-for="(image, index) in product.images"
            :key="image"
            @click="setImageByIndex(index, product.images)"
            class="w-20 h-20 border rounded-md overflow-hidden shrink-0"
            :class="
              selectedImage === image
                ? 'border-black'
                : 'border-gray-200'
            "
          >
            <img
              :src="image"
              class="w-full h-full object-cover"
            />
          </button>
        </div>

      </div>

      <!-- Product Information -->
      <div class="lg:sticky lg:top-24 h-fit">

        <h1 class="text-3xl md:text-4xl font-semibold text-gray-900">
          {{ product.name }}
        </h1>

        <p class="text-2xl font-medium mt-4 text-gray-900">
          {{ product.price }}
        </p>

        <p
          v-if="product.description"
          class="mt-6 text-gray-600 leading-relaxed"
        >
          {{ product.description }}
        </p>

        <!-- Size Selection -->
        <div v-if="product.sizes?.length" class="mt-8">

          <h3 class="font-medium mb-3">Size</h3>

          <div class="flex flex-wrap gap-3">
            <button
              v-for="size in product.sizes"
              :key="size"
              @click="selectedSize = size"
              class="h-12 min-w-[56px] px-4 border transition-all"
              :class="
                selectedSize === size
                  ? 'bg-black text-white border-black'
                  : 'border-gray-300 hover:border-black'
              "
            >
              {{ size }}
            </button>
          </div>
        </div>

        <!-- Quantity -->
        <div class="mt-8">

          <h3 class="font-medium mb-3">Quantity</h3>

          <div class="flex items-center border border-gray-300 w-fit">
            <button
              @click="decreaseQty"
              class="w-12 h-12 text-xl hover:bg-gray-100"
            >
              −
            </button>

            <span class="w-12 text-center">
              {{ quantity }}
            </span>

            <button
              @click="increaseQty"
              class="w-12 h-12 text-xl hover:bg-gray-100"
            >
              +
            </button>
          </div>

        </div>

        <!-- Buttons -->
        <div class="mt-8 space-y-3">

          <button
            class="w-full bg-[#1d1d1d] text-white py-4 rounded-md hover:opacity-90 transition"
          >
            Add To Cart
          </button>

        </div>

      </div>

    </div>

    <!-- Related Products -->
    <div class="mt-24 -mx-6 md:-mx-12">
        <ProductGrid
            :products="relatedProducts"
            title="Related Products"
            tag="#related"
            :showViewAll="false"
        />
    </div>

  </section>
</template>