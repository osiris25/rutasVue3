<script setup>
import { useRoute, useRouter } from "vue-router";
import { ref } from "vue";
import { useGetData } from "@/composable/getData";
import { useFavoritosStore } from "@/store/favoritos.js";

const route = useRoute();
const router = useRouter();
const useFavoritos = useFavoritosStore();
const { add, findPoke } = useFavoritos;
console.log(findPoke);

const { data, getData, loading, error } = useGetData();

const back = () => {
  router.push("/pokemons");
};
getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`);
</script>

<template>
  <div class="container-fluid">
    <div class="row">
      <div class="container">
        <div class="col-12">
          <div v-if="loading">
            <p>Cargando ....</p>
          </div>
        </div>
      </div>
    </div>

    <div class="row">
      <div class="container">
        <div class="col-12 mt-2" v-if="error">
          <p class="alert alert-danger fs-2">{{ error }}</p>  
          <img class="img-fluid" src="@/assets/pokemon-triste.jpeg" alt="error">
        </div>
        <div class="col-12 d-flex justify-content-center m-5" v-if="data">
          <div class="card mb-3" >
            <div class="row g-0">
              <div class="col-md-4">
                <img :src="`${data.sprites.other.dream_world.front_default}`" width="350"
                height="350" class="img-fluid rounded-start" alt="...">
              </div>
              <div class="col-md-8">
                <div class="card-body">
                  <h5 class="card-title text-uppercase">{{data.id }}-{{ $route.params.name }}</h5>
                  <ul class="list-group list-group-flush">
                    <li class="list-group-item">Peso:{{data.weight}}</li>
                    <li class="list-group-item">Altura:{{ data.height}}</li>
                    <li class="list-group-item">Experiencia: {{ data.base_experience}}</li>        
                  </ul>
                  <div col-12>
                  <button
                :disabled="findPoke(data.name)"
                class="btn btn-primary"
                @click="add(data)"
              >Agregar Favoritos</button>
                </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="col-12 m-4">
          <button @click="back" class="btn btn-outline-primary">Volver</button>
</div>    
      </div>
    </div>
  </div>
</template>