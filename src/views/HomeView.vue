<script setup>
import { useCounterStore } from "@/store/counter.js";
import { storeToRefs } from "pinia";
const useCounter = useCounterStore();
const { increment } = useCounter; //desdestructuracion
const { double, count } = storeToRefs(useCounter);
</script>

<template>
  <div class="container justify-content-center">
    <div class="row">
      <div class="container">
        <div class="col-12">
           <h1>
            BIENVENIDO AL MUNDO POKEMON
           </h1> 
        </div>
        <div class="col-12">
            <img width="100%" height="100%" src="@/assets/mundo.webp"/>
        </div>
      </div>

      <!-- <div class="col-12 m-2">
            <h1>Home counter:{{count}}</h1>
        </div>
        <div class="col-12 m-2">
            <h2>Double:{{ double}}</h2>
        </div>
        <div class="col-12">
            <button class="btn btn-lg btn-primary" @click="increment">Incremet</button>
      </div>-->
    </div>
  </div>
</template>

