<template>
  <div class="opcionesContainer">
    <ul>
      <li
        v-for="pokemon in pokemons"
        :key="pokemon.id"
        @click="$emit('seleccionPokemon', 
        {ident: pokemon.id, 
        nombre: pokemon.nombre,
        test: 'esto es una prueba',
        test2: test3
        })"
      >
        {{ pokemon.nombre }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  components: {},
  props: {
    pokemons: {
      type: Array,
      required: true,
    },
  },

  data() {
    return {
      test3: "esto es una prueba",
    };
  },
};
</script>

<style scope>
.opcionesContainer {
  display: flex;
  justify-content: center;
}

ul {
  list-style-type: none;
}

li {
  border: 1px solid rgb(rgb(48, 28, 28), rgb(132, 198, 132), blue);
  border-radius: 5px;
  cursor: pointer;
  margin-bottom: 10px;
  width: 250px;
  background-color: white;
}

li:hover {
  background-color: rgb(132, 198, 132);
}
</style>