<script setup>
    const pokemon = defineProps(["name", "url"])
    const pokemonId = pokemon.url.split('/')[6]
    const imageUrl = `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${pokemonId}.svg`
</script>

<template>
    <div class="col-md-4">
        <div class="card p-2 mb-3">
            <img :src="imageUrl" height="80" alt="">
            <p class="text-center">{{ pokemon.name }}</p>
        </div>
    </div>
</template>

<style>

</style>