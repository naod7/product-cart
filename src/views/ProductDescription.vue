<script setup>
import products from '@/data/products.json'
import {useRoute} from 'vue-router'
import {defineProps} from 'vue'
import {ref} from 'vue'

const {addToCart} = defineProps(['addToCart'])

const route = useRoute()

const productId = parseInt(route.params.id)

const productDetail = products.find((p)=>{
    return p.id === productId
})


const quantity = ref(0)
</script>


<template>
    <section class="py-5">
        <div class="container px-4 px-lg-5 my-5">
            <div class="row gx-4 gx-lg-5 align-items-center">
                <div class="col-md-6"><img class="card-img-top mb-5 mb-md-0" :src="productDetail.icon" alt="..." /></div>
                <div class="col-md-6">
                    <div class="small mb-1">SKU: BST-498</div>
                    <h1 class="display-5 fw-bolder">{{ productDetail.name }}</h1>
                    <div class="fs-5 mb-5">
                        <span class="text-decoration-line-through">{{ productDetail.Price  }}</span>
                        <span>{{ productDetail.Price  }}</span>
                    </div>
                    <p class="lead">Lorem ipsum dolor sit amet consectetur adipisicing elit. Praesentium at dolorem quidem modi. Nam sequi consequatur obcaecati excepturi alias magni, accusamus eius blanditiis delectus ipsam minima ea iste laborum vero?</p>
                    <div class="d-flex">
                        <div class="cell">
                            <input id="inputQuantity" type="num" v-model.number="quantity"/>
                        </div>
                        <button class="btn btn-dark" type="button" @click="addToCart(productDetail.name, quantity)">
                            <i class="icofont-cart-alt icofont-1x"></i>
                            Add to cart
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>