<template>
    <div>
        <h1>Shopping Cart</h1>
        <ul>
            <li v-for="product in products" :key="product.title">
                {{product.title}} - {{product.price}} - {{product.quantity}}
            </li>
        </ul>
    </div>
</template>

<script>
import store from '../store/index.js'

export default {

    computed:{
        products(){
            return store.getters.cartProducts
        }
    }
    
}
</script>
