<script setup>
// import axios from "axios";
import { useRoute, useRouter } from "vue-router";
import { ref } from "vue";
import {useGetData} from "@/composable/getData";
const route = useRoute();
const router = useRouter();
// const pokemon = ref({});
const {data, getData,loading, error}=useGetData();
// const getData = async () => {
//   try {
//     console.log(`${route.params.name}`, "rutas");
//     const { data } = await axios.get(
//       `https://pokeapi.co/api/v2/pokemon/${route.params.name}`
//     );
//     pokemon.value = data;
//     console.log(data);
//   } catch (error) {
//     console.log(error);
//     pokemon.value = null;
//   }
// };
// const back=()=>{
// router.push("/pokemons");
// }
getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`);
</script>
<template>
  <div class="container-fluid">
    <div v-if="loading">
      <p>Cargando ....</p>
    </div>
    <div class="alert alert-danger" v-if="error">{{ error }}</div>
    <div v-if="data">
      <h1>nombre pokemon:{{ $route.params.name }}</h1>
      <div class="card" style="width: 18rem;">
        <img :src="`${data.sprites.front_default}`" class="card-img-top" alt="..." />
        <div class="card-body">
          <h5 class="card-title">{{data.species.name}}</h5>
          <p
            class="card-text"
          >Some quick example text to build on the card title and make up the bulk of the card's content.</p>
          <a href="#" class="btn btn-primary">Go somewhere</a>
        </div>
      </div>
    </div>
    <button @click="back" class="btn btn-outline-primary">Volver</button>
  </div>
</template>