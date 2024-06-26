<template>
    <div class="pokemonContainer">
      <img v-show="!mostrarPokemon" class="ocultarPokemon" :src="imagenFuente" alt="No hay imagen" />
      <img v-show="mostrarPokemon" :src="imagenFuente" alt="No hay imagen" />
    </div>
  </template>
  <script>
  export default {
    data() {
      return {
        mostrar: false,
      };
    },
    props: {
      idPokemon: {
        type: Number,
        required: true,
      },
      mostrarPokemon: {
        type: Boolean,
        required: true,
      },
    },
    computed: {
      imagenFuente() {
        return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.idPokemon}.svg`;
      },
    },
  };
  </script>
  
  <style scoped>
  .ocultarPokemon {
    filter: brightness(0);
  }
  img {
    height: 200px;
    width: 200px;
    position: absolute;
    right: 45%;
  }
  .pokemonContainer {
    height: 200px;
  }
  </style>