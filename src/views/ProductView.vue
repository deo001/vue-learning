<script setup>
import {useRoute} from 'vue-router'
import {ref,onBeforeMount} from 'vue'
import products from "../data.json"

const product = ref(null)
const route = useRoute()
const {id} = route.params
onBeforeMount(()=> {
    product.value = products.find(p => p.id === parseInt(id))
})


</script>
<template>

    <div class="container justify-content-center text-align-center">
        <div v-if="product" class="align-items-center">
            <h1> product  details</h1>
            <h3>{{ product.name}}</h3>
            <p>{{ product.price }}</p>
        </div>
        <div v-else>
            <h1>Nothing to show</h1>
        </div>
    
    </div>
</template>
