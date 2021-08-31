<template>
  <h2 v-if="!pokemon">Espere por favor...</h2>

  <div v-else>
    <h2>¿Quién es este pokémon?</h2>
    <PokemonPicture :pokemonId="pokemon.id" :showPokemon="showPokemon" />
    <PokemonOptions :pokemons="pokemonArr" @selectionPokemon="checkAnswer"/>

    <div v-if="showAnswer">
      <h4 class="fade-in mb-3">{{ message }}</h4>
      <button class="fade-in btn btn-dark mb-5 px-3" @click="newGame">Nuevo Juego</button>
    </div>
  </div>
</template>

<script>
import PokemonPicture from '@/components/PokemonPicture'
import PokemonOptions from '@/components/PokemonOptions'

import getPokemonOptions from '@/helpers/getPokemonOptions'

export default {
  name: 'PokemonPage',
  components: {
    PokemonPicture,
    PokemonOptions
  },
  data() {
    return {
      pokemonArr: [],
      pokemon: null,
      showPokemon : false,
      showAnswer: false,
      message: ''
    };
  },
  mounted() {
    
  },
  methods: {
    async mixPokemonArray() {
      this.pokemonArr = await getPokemonOptions()
      const rndInt = Math.floor(Math.random() * 4)
      this.pokemon = this.pokemonArr[ rndInt ]
    },
    checkAnswer(pokemonId){
      this.showPokemon = true
      this.showAnswer = true
      
      if(pokemonId === this.pokemon.id){
        this.message = `Correcto, es ${this.pokemon.name}`
      }else{
        this.message = `Ups, era ${this.pokemon.name}`
      }
      
    },
    newGame(){
      this.showPokemon = false
      this.showAnswer = false
      this.pokemonArr = []
      this.pokemon = null
      this.mixPokemonArray()
    }
  },
  mounted() {
    this.mixPokemonArray()
  }
};
</script>

<style scoped>
h2 , h4 {
  font-weight: 600;
}
button:hover {
  background-color: #646464;
  border-color: #646464;
}
</style>