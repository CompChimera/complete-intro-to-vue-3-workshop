<script>
//https://pokeapi.co/api/v2/pokemon?limit=151
import Pokedex from './components/Pokedex.vue'

export default {
  components: {
    Pokedex,
  }
}
</script>

<template>
  <h1> New App</h1>
  <Suspense>
    <Pokedex />

    <template v-slot:fallback >
      Loading Pokedex Data...
    </template>
  </Suspense>
</template>

<style></style>