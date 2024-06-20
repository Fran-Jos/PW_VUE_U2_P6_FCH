<template>
  <div class="pokemonContainer">
    <img
      v-show="mostrar"
      src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/1.svg"
      alt="no se pudo visualizar la imagen"
    />

    <img
      v-show="!mostrar"
      class="ocultaPokemon"
      src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/1.svg"
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