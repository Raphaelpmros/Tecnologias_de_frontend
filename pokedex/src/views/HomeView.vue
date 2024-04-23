<script setup>
import { onMounted, reactive, ref } from 'vue';
import ListPokemon from '../components/ListPokemon.vue';

let pokemons = reactive(ref());

onMounted(() => {
  fetch("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0")
  .then(response => response.json())
  .then(response => {
    pokemons.value = response.results
    console.log(pokemons)
  })
})

</script>

<template>
  <main>
    <div class="container">
      <div class="row mt-4">
        <div class="col-sm-12 col-md-6">
          <div class="card" style="width: 25rem;">
            <img src="https://assets.pokemon.com/assets/cms2/img/pokedex/full/025.png" class="card-img-top" alt="...">
            <div class="card-body">
              <h5 class="card-title">Card title</h5>
              <p class="card-text">Algum texto aletório e pequeno aqui.</p>
            </div>
          </div>
        </div>
        <div class="col-sm-12 col-md-6">
          <div class="card">
            <div class="card-body row">
              <ListPokemon 
                v-for="pokemon in pokemons" 
                :key="pokemon.name"  
                :name="pokemon.name"
                :url="pokemon.url" 
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>
