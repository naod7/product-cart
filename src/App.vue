
<script setup>
import SideBar from '@/components/SideBar.vue'
import {ref} from 'vue'

const showSideBar = ref(false)

function toggleSide(){
  showSideBar.value = !showSideBar.value
}

const cart = ref({})
function addToCart(name, quantity){
  if(!cart.value[name]){
    cart.value[name] = 0
  }

  cart.value[name]+= quantity

}

</script>


<template>
  <header class="top-bar spread">
    <nav class="top-bar-nav">
      <router-link to="/" class="top-bar-link">
        <i class="icofont-spoon-and-fork"></i>
        <span>Home</span>
      </router-link>
      <router-link to="/products" class="top-bar-link">
        <span>Products</span>
      </router-link>
      <router-link to="/past-orders" class="top-bar-link">
        <span>Past Orders</span>
      </router-link>
      <a class="top-bar-cart-link" @click="toggleSide">
        <i class="icofont-cart-alt icofont-1x"></i>
        <span>Cart (0)</span>
      </a>

    </nav>
  </header>
  <SideBar
    v-if="showSideBar"
    :toggleSide="toggleSide"
    :cart="cart"
  />
  <router-view
  :addToCart="addToCart"
  />
</template>


<style>

/*#header {
    display: flex;
    align-items: center;
    height: 35px;
    background: linear-gradient(90deg, #1f0c25 1.18%, #6d002a 100%);
    color: white;
    padding: 20px;

    text-decoration: none;
}
#header.header-scrolled {
  border-color: #fff;
  box-shadow: 0px 2px 15px rgba(18, 66, 101, 0.08);
}

.top-bar{
    background: linear-gradient(90deg, #1f0c25 1.18%, #6d002a 100%);
    color: white;
    font-size: 0px;
    padding: 5px;
  }

.top-bar-nav{
  display: flex;
  align-items:center;

}




.top-bar-link   {
      display: flex;
      border-right: 1px solid white;
      padding: 15px 19px;
      color: white;
      font-size: 16px;
      text-decoration: none;
      justify-content:space-between;

}

.top-bar-cart-link{
      display: flex;
      padding: 15px 19px;
      color: white;
      font-size: 16px;
      text-decoration: none;
      justify-content:space-around;
      align-items: center;


}



.top-bar-link{
    display: inline-block;
    text-decoration: none
}
i:first-of-type span:hover{
    margin-left: 10px;
    color: white;
    font-size: 40px;
    text-decoration: none;
    vertical-align: -8px;
    padding-left: 10px;
    background: #9ABA00

}

  .top-bar-cart-link span :hover span i,
      :hover i{
    text-decoration: none;
    cursor: default;
    border: 0px;
    font-size: 16px;
    text-decoration: underline;
    margin-right: -7px;
    color: white;
    font-size: 31px;
    text-decoration: none;
    vertical-align: -4px;
  }

*/



</style>

