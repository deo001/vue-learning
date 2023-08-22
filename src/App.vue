<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <nav class = "navbar navbar-expand-lg navbar-primary bg-white py-4 fixed-top">
  <div class = "container">
      <a class = "navbar-brand d-flex justify-content-between align-items-center order-lg-0" href = "index.html">
          <img src="../src/assets/images/shopping-bag-icon.png" alt="">
          <span class = "text-uppercase fw-lighter ms-2">Brellah</span>
      </a>
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
                  <RouterLink to="/"  class="text-black text-uppercase">Home</RouterLink>
              </li>
              <li class = "nav-item px-2 py-2">
                  <router-link to="/collections" class="text-black">COLLECTIONS</router-link>
              </li>
              <li class = "nav-item px-2 py-2">
                  <RouterLink to="/"  class="text-black text-uppercase">Specials    </RouterLink>
              </li>
              <li class = "nav-item px-2 py-2">
                  <RouterLink to="/"  class="text-black text-uppercase">Blogs</RouterLink>
              </li>
              <li class = "nav-item px-2 py-2">
                  <RouterLink to="/about"  class="text-black text-uppercase">About</RouterLink>
              </li>
              <li class = "nav-item px-2 py-2 border-0">
                  <RouterLink to="/popular"  class="text-black text-uppercase   ">POPULAR</RouterLink>
              </li>
          </ul>
      </div>
  </div>
</nav>

  <RouterView />
</template>

<style>
.bg-primary{
    background-color: var(--pink)!important;
}

.btn:not(.nav-btns button){
    background-color: #fff;
    color: rgb(85, 85, 85);
    padding: 10px 28px;
    border-radius: 25px;
    border: 1px solid rgb(85, 85, 85);
}
.btn:not(.nav-btns button):hover{
    background-color: var(--pink);
    color: #fff;
    border-color: var(--pink);
}

/* text color */
.text-primary{
    color: var(--pink)!important;
}

/* navbar */
.navbar{
    -webkit-box-shadow: 0 3px 9px 3px rgba(0, 0, 0, 0.1);
            box-shadow: 0 3px 9px 3px rgba(0, 0, 0, 0.1);
}
.navbar-brand img{
    width: 30px;
}
.navbar-brand span{
    letter-spacing: 2px;
    font-family: var(--lg-font);
}
.nav-link:hover{
    color: var(--pink)!important;
}
.nav-item{
    border-bottom: 0.5px solid rgba(0, 0, 0, 0.05);
}
</style>