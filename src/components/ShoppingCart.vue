<template>
    <div>
        <h1>Shopping Cart</h1>
        <ul>
            <li v-for="product in products" :key="product.title">
                {{product.title}} - {{product.price | currency}} - {{product.quantity}}
            </li>
        </ul>
        <p>Total: {{total | currency}}</p>
        <button @click="$store.dispatch('checkout')">Checkout</button>
      <p v-if="$store.state.checkoutStatus">{{$store.state.checkoutStatus}}</p>
    </div>
</template>

<script>
import store from '../store/index.js'

export default {


    computed:{
        products(){
            return store.getters.cartProducts
        },
        total(){
            return store.getters.cartTotal
        }
    },

    
    
}
</script>
