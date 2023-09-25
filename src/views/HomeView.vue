<script setup>
//import '@/assets/style.css'
  import products from '@/data/products.json'
  import {ref, watch} from "vue"
  import ProductCard from '@/components/ProductCard.vue'
  import {defineProps} from 'vue'

  const cards = ref(products)
  const {addToCart} = defineProps(['addToCart'])

</script>

<template>


    <div class="splash-container">
        <div class="splash">
          <h1>NG Store</h1>
        </div>
    </div>
    <main class="wrapper">

        <h2>Recommended</h2>

        <div class="recommended">
          <div class="card-container">
            <ProductCard
              v-for="card in cards.slice(0, 6)"
              :key="card.id"
              :card="card"
              :addToCart="addToCart"
            />
          </div>
        </div>
    </main>
</template>

