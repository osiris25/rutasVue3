<script setup>
import {useCounterStore} from "@/store/counter.js";
const userCounter = useCounterStore();
</script>

<template>
 <h1>Home counter:{{  }}</h1>
</template>

