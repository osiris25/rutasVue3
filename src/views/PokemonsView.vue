<template>
    <div class="container">
        <ul v-for="(pokemon, index) in pokemons" :key="index">
           <router-link :to="`/pokemons/${pokemon.name}`">{{ pokemon.name }}</router-link> 
        </ul>
        <!-- <div class="card" style="width: 18rem;" v-for="(pokemon, index) in pokemons" :key="index">
            <img :src="`${pokemon.url}`" class="card-img-top" alt="...">
            <div class="card-body">
              <h5 class="card-title">{{pokemon.name}}</h5>
              <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
              <a href="#" class="btn btn-primary">Go somewhere</a>
            </div>
          </div> -->
    </div>
</template>
<script setup>
import axios from 'axios';
import {ref} from 'vue';
import {RouterLink} from 'vue-router'
const pokemons = ref([])
const getData = async ()=>{
    try{
       const {data}= await axios.get('https://pokeapi.co/api/v2/pokemon');
       pokemons.value = data.results;
    }catch(error){
        console.log(error);;
    }
}
getData()
</script>