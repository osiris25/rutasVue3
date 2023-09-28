<script setup>
// import axios from 'axios';
import {ref} from 'vue';
import {RouterLink} from 'vue-router'
import{useGetData} from '@/composable/getData'
const pokemons = ref([])
const {data, getData, loading} = useGetData();
// const getData = async ()=>{
//     try{
//        const {data}= await axios.get('https://pokeapi.co/api/v2/pokemon');
//        pokemons.value = data.results;
//     }catch(error){
//         console.log(error);;
//     }
// }
getData("https://pokeapi.co/api/v2/pokemon")

</script>
<template>
    <div class="container">
      <div v-if="loading">
        <p>Cargando ....</p>
      </div>
      <div class="alert alert-danger" v-if="error">{{ error }}</div>
      <div v-if="data">
         <div><h1>Lista Pokemones</h1></div>
         <div>
          <ul class="list-group" v-for="(pokemon, index) in data.results" :key="index">
            <li class="list-group-item text-lowercase fs-4 ">
              <router-link :to="`/pokemons/${pokemon.name}`">{{ pokemon.name }}</router-link> 

            </li>
        </ul>
         </div>
        <div>
          <button 
          class="btn btn-outline-primary me-2" 
          @click="getData(data.previous)"
          :disabled="!data.previous">Previous</button>
          <button 
          class="btn btn-outline-primary" 
          @click="getData(data.next)"
          :disabled="!data.next">Next</button>

        </div>
      </div>
     
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