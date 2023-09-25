
<script setup>

import ProductCard from '@/components/ProductCard.vue'
import products from '@/data/products.json'
import {defineProps} from 'vue'
import {ref, watch} from "vue"

const {addToCart} = defineProps(['addToCart'])
const cards = ref(products)
const searchProduct = ref('Search............')


watch(searchProduct, ()=>{
  cards.value = products.filter((p)=>{
    return p.name.toLowerCase().includes(searchProduct.value.toLowerCase())
  })

})

</script>



<template>
  <main class="wrapper">
    <input type="search"  class="inputSearch" v-model="searchProduct"/>
    <h1>Products</h1>

    <div class="card-container">
      <ProductCard
        v-for="card in cards.slice(0, 6)"
        :key="card.id"
        :card="card"
        :addToCart="addToCart"
      />
    </div>
  </main>
</template>