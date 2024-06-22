<template>
  <div class="pokemonContainer">
    <img
      v-show="mostrarPokemon"
      :src="imagenFuente"
      alt="no se pudo visualizar la imagen"
    />

    <img
      v-show="!mostrarPokemon"
      class="ocultaPokemon"
      :src="imagenFuente"
      alt="no se pudo visualizar la imagen"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      mostrar: false,
  
    };
  },
  props:{
    idPokemon:{
      type: Number,
      required: true
    },
    mostrarPokemon:{
      type:Boolean,
      required:true,
      default:true

    }
  },

  computed:{
    imagenFuente(){
      return "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/"+ this.idPokemon +".svg";
      //return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/$(this.idPokemon).svg`
      
    }
  }
};
</script>

<style scoped>
.ocultaPokemon {
  filter: brightness(0);
}
img {
  height: 200px;
  width: 200px;
  position: absolute;
  right: 42%;
}
.pokemonContainer {
  height: 200px;
}
</style>