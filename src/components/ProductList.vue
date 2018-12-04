<template>
    <div>
        <h1>Product List</h1>
        <img v-if="loading" src="https://i.imgur.com/JfPpwOA.gif" alt="">
        <ul class="list-group" v-else>
            <li class="list-group-item" v-for="product in products" :key="product.id">
                {{product.title}} - {{product.price}} - {{product.inventory}}
                <button class="btn btn-info" @click="addProductToCart(product)">Add to cart</button>
            </li>  
        </ul>
    </div>
</template>

<script>

import store from '@/store/index'

export default {

    data(){
        return{
            loading:false,
        }
    },

    computed:{
        products(){
            return store.getters.availableProducts
        }
    },

    created(){
        this.loading = true;
        store.dispatch('fetchProducts').then(()=>this.loading = false) 
        // dispatch is similar to commit but for events actions instead
    },

    methods:{
        addProductToCart(product){
            store.dispatch('addProductToCart',product)
        }
    }
    
}
</script>

