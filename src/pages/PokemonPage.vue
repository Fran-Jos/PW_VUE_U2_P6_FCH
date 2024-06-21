<template>
<PokemonImagenVue :idPokemon="6" :mostrarPokemon="true"/>
<PokemonOpcionesVue :pokemons="arreglo"/>
</template>

<script>

import PokemonImagenVue from "../components/PokemonImagen.vue";
import PokemonOpcionesVue from "../components/PokemonOpciones.vue";
import obtenerPokemonsFachada  from "../clientes/clientePokemonApi.js";
export default {
    data() {
    return {
      arreglo:[],
  
    };
  },
  mounted(){
     this.cargaInicial();
  },
components:{
  PokemonImagenVue,
  PokemonOpcionesVue
},

methods:{
  async cargaInicial(){
    const vectorInicial = await obtenerPokemonsFachada(4);
    this.arreglo = vectorInicial;
  }
}
}
</script>

<style>

</style>