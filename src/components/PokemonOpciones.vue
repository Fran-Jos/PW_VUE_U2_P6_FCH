<template>
  <div class="opcionesContainer">
    <li v-for="pokemon in pokemons" :key="pokemon.id" @click="$emit('seleccionPokemon',{
        ident:pokemon.id,
        nomb:pokemon.nombre,
    })" >
        {{ pokemon.nombre}}</li>
  </div>
</template>

<script>
export default {
  props: {
    pokemons: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style>
ul {
  list-style-type: none;
}
li {
  display: flex;
  border: 1px solid black;
  border-radius: 5px;
  margin-bottom: 10px;
  width: 250px;
  background: white;
  cursor: pointer;
  justify-content: center;

}
li:hover {
  background: rgba(0, 0, 0, 0.09);
}
.opcionesContainer {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  
  
  
}
</style>