<script setup>
import {ref} from 'vue'
</script>

<template>
  <nav class="navbar bg-dark text-white" data-bs-theme="white">
    <div class="container">
      <ul class="nav">
        <li class="nav-item">
          <router-link class="navbar-brand" to="/"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/b1/Rick_and_Morty.svg/800px-Rick_and_Morty.svg.png" class="logo"></router-link>
        </li>
        <li class="nav">
          <router-link class="nav-link" aria-current="page" to="/">Início</router-link>
        </li>
        <li class="nav">
          <router-link class="nav-link" to="/about">Sobre</router-link>
        </li>
      </ul>
    </div>
  </nav>
  
  <div class="main">
    <router-view></router-view>
  </div>

 
</template>
<style>
  .logo{
    width: 8rem;
    margin-left: -10px;
    margin-top: 1px;
  }

  .nav-link{
    color: #FFFFFF
  }

</style>


