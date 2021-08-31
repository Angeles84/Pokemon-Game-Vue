<template>
  <div class="pokemon-container mt-4 mt-md-5">
    <img v-if="!showPokemon" :src="imgSrc" class="fade-in hidden-pokemon" alt="pokemon">
    <img v-else :src="imgSrc" class="fade-in" alt="pokemon">
  </div>
</template>

<script>
export default {
  name: 'PokemonPicture',
  props: {
    pokemonId: {
      type: Number,
      required: true
    },
    showPokemon: {
      type: Boolean,
      required: true,
      default: false
    }
   },
  data() {
    return {
      
    };
  },
  computed: {
    imgSrc() {
      return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokemonId}.svg`
    }
  },
  methods: {
    
  },
};
</script>

<style scoped>
.pokemon-container {
    height: 190px;
}
img {
    height: 160px;
    user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    -webkit-user-drag: none;
    -webkit-user-select: none;
    transition: all 0.7s ease;
}
.hidden-pokemon {
    filter: brightness(0);
}
</style>