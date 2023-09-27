<script setup>
import axios from 'axios';
import { useRoute } from 'vue-router';
import { ref } from 'vue';

const route = useRoute();
const pokemon =ref({})
const getData = async()=>{
    try{
        console.log(`${route.params.name}`, "rutas");
        const {data}= await axios.get( `https://pokeapi.co/api/v2/pokemon/${route.params.name}`)
        pokemon.value = data
        console.log(data);
        
    }catch(error){
console.log(error);
    }
};
getData()
</script>
<template>
    <div>
     <h1>
        nombre pokemon:{{ $route.params.name }}
    </h1>
      <div class="card" style="width: 18rem;">
        <img :src="`${pokemon.sprites.front_default}`" class="card-img-top" alt="...">
        <div class="card-body">
          <h5 class="card-title">{{pokemon.species.name}}</h5>
          <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
          <a href="#" class="btn btn-primary">Go somewhere</a>
        </div>
      </div>    
    </div>
   
</template>