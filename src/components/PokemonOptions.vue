<template>
  <div class="options-container mt-0 mt-md-3">
  <ul class="pl-0">
    <li v-for="pokemon in pokemons" :key="pokemon.id" @click="$emit('selectionPokemon', pokemon.id)">
      {{ pokemon.name }}
    </li>
  </ul>
  </div>
</template>

<script>
export default {
  name: 'PokemonOptions',
  props: {
    pokemons: {
      type: Array,
      required: true
    }
  }
};
</script>

<style scoped>
ul {
    list-style-type: none;
    margin-bottom: 15px;
}
li {
    background-color: white;
    border-radius: 5px;
    border: 1px solid rgba(0, 0, 0, 0.2);
    cursor: pointer;
    margin-bottom: 13px;
    width: 250px;
    padding-top: 4px;
    padding-bottom: 4px;
    transition: all 0.5s ease;
}

li:hover {
    background-color: rgba(0, 0, 0, 0.2);
}

.options-container {
    display: flex;
    justify-content: center;
}

</style>