<script setup>
import productDetails from "../data.json"
import {ref, watch, onMounted} from "vue"
import { RouterLink, RouterView } from 'vue-router'
import {useRouter, useRoute} from 'vue-router'

const route = useRoute()
const router = useRouter()

const products = ref(productDetails)

const name = ref("")
onMounted(() =>{ 
    name.value = route.query.name
})

watch(name, () =>{
    if (name.value) {
        if(name.value === "All") products.value = productDetails;
        else{
            products.value = productDetails.filter(c => c.name === name.value)
        }
    }
})

const handleChange = () =>{
    router.push({query:{name: name.value}})
}
</script>

<template>
    <nav class = "navbar navbar-expand-lg  bg-light py-2 fixed-top">
    <div class = "container">
        <RouterLink class = "navbar-brand d-flex justify-content-between align-items-center order-lg-0" to = "/">
            <img src="../src/assets/images/shopping-bag-icon.png" alt="">
            <span class = "text-uppercase fw-lighter text-primary ms-2">Brellah</span>
        </RouterLink >
        <div class = "order-lg-2 nav-btns">
            <button type = "button" class = "btn position-relative">
                <i class = "fa fa-shopping-cart"></i>
                <span class = "position-absolute top-0 start-100 translate-middle badge bg-primary">5</span>
            </button>
            <button type = "button" class = "btn position-relative">
                <i class = "fa fa-heart"></i>
                <span class = "position-absolute top-0 start-100 translate-middle badge bg-primary">2</span>
            </button>
            <button type = "button" class = "btn position-relative">
                <i class = "fa fa-search"></i>
            </button>
        </div>

        <button class = "navbar-toggler border-0" type = "button" data-bs-toggle = "collapse" data-bs-target = "#navMenu">
            <span class = "navbar-toggler-icon"></span>
        </button>

        <div class = "collapse navbar-collapse order-lg-1" id = "navMenu">
            <ul class = "navbar-nav mx-auto text-center">
                <li class = "nav-item px-2 py-2">
                    <RouterLink active-class="active " to="/"  class="text-black text-uppercase">Home</RouterLink>
                </li>
                <li class = "nav-item px-2 py-2">
                    <router-link active-class="active " to="/collections" class="text-black">COLLECTIONS</router-link>
                </li>
                
                <li class = "nav-item px-2 py-2">
                    <RouterLink active-class="active " to="/about"  class="text-black text-uppercase">About</RouterLink>
                </li>
                <li class = "nav-item px-2 py-2 border-0">
                    <RouterLink active-class="active " to="/popular"  class="text-black text-uppercase   ">POPULAR</RouterLink>
                </li>
            </ul>
        </div>
    </div>
    </nav>
<main class="container-product m-5">
    <h1 class="text-center">our products</h1> 
    <select 
    @change="handleChange"
    v-model="name" > 
        <option value="All"> All</option>
        <option value="brazilian coat"> Brazilian Shirt</option>
        <option value="shirt"> Normal Shirt</option>
        <option value="tz coat"> Tz coat</option>
        <option value="jk coat"> jk Shirt</option>
    </select> 
    <div class="cards">
        <div class="card-bodys" 
        v-for="product in products" 
        :key="product.id"
        @click="router.push(`/product/${product.id}`)"
    >
            <h4 class="card-title">{{ product.name }}</h4>
            <p class="card-text">{{ product.price }}</p>
        </div>
    </div>
</main>

  <RouterView />
</template>

<style>
.cards{
    display: flex;
    width: 100%;
    flex-wrap: wrap;
    margin-top: 50px;
    justify-content: center;
}
.card-bodys{
    box-shadow: 1px 1px 1px rgba(0,0,0,0.207);
    padding: 10px;
    width: 200px;
    margin-right: 20px;
    cursor: pointer;
    margin-bottom: 20px;
}
.active{
    
    background-color: #8f8f8f;
    padding: 8 px;

}

</style>