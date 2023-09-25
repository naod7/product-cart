
<script setup>
import {defineProps} from 'vue'
import {useRouter} from 'vue-router'
import {ref} from 'vue'
const {card, addToCart} = defineProps(['card', 'addToCart'])

const router = useRouter()

function cardDescription(){
  router.push(`product/${card.id}`)
}

const quantity = ref(0)

</script>


<template>


    <div class="card" >
        <div class="card-title">
            {{ card.name }}
        </div>
        <div class="card-body">
            <img :src="card.icon" class="card-img" @click="cardDescription">
            <form>
                <div class="row">
                    <div class="cell">
                      <label>Type:</label>
                    </div>
                    <div class="cell">
                      <em>{{ card.type }}</em>
                    </div>
                </div>
                <div class="row">
                    <div class="cell">
                      <label>Price:</label>
                    </div>
                    <div class="cell">
                      ${{ card.Price }}
                    </div>
                </div>
                <div class="row">
                    <div class="cell">
                      <label>Quantity:</label>
                    </div>
                    <div class="cell">
                      <input type="number"  v-model.number="quantity">
                    </div>
                </div>
            </form>
        </div>
        <div class="card-footer">
            <button class="btn btn-light" @click="addToCart(card.name, quantity)">Add to cart</button>
        </div>
    </div>

</template>