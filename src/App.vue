<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div>
    <nav class="navbar bg-body-tertiary">
      <div class="container">
        <router-link class="navbar-brand" to="/">
          <img src="@/assets/logo.svg" alt="Bootstrap" width="30" height="24">
          POKE API
        </router-link>
      <div>
        <router-link class="btn btn-outline-primary me-2" to="/">Home</router-link>
        <router-link  class="btn btn-outline-primary" to="/pokemons">Pokemons</router-link>
      </div>
      </div>
    </nav>
  </div>
  

  <RouterView />
</template>

