<script setup>
import { useFavoritosStore } from "@/store/favoritos";
import { storeToRefs } from "pinia";
import { RouterLink } from "vue-router";

const useFavoritos = useFavoritosStore();
//el storeToRefs solo es para los getters o datos reactivos
const { favoritos } = storeToRefs(useFavoritos);
console.log(favoritos.value, "favoritos");
//los metodos se desestructuran directamente de la funcion useNombreStore
const { remove } = useFavoritos;
</script>
<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-12 d-flex justify-content-center" v-if="!favoritos">
        <div class="col-8 m-1 alert alert-warning" role="alert">
          <p>No existen pokemones favoritos</p>
        </div>
      </div>
      <div class="col-12 d-flex flex-wrap">
        <div class="col-4 mb-2 mt-2" v-for=" poke in favoritos" :key=" poke.id">
          <div class="card">
            <div class="card-header text-capitalize fw-bold fs-3">
            <button type="button" class="position-absolute top-0 end-0 btn-close" aria-label="Close" @click="remove(poke.id)"></button>

                {{poke.name}}
            </div>
            <div class="card-body">
              <div class="col-12">
                <img
                  class="rounded-circle"
                  width="250"
                  height="250"
                  :src="`${poke.sprites.other.dream_world.front_default}`"
                  alt
                />
              </div>
              <div col-12>
                <router-link
                  class="btn btn-danger me-2"
                  :to="`/pokemons/${poke.name}`"
                >Más información</router-link>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>