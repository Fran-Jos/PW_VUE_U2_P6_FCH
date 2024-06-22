<template>
  <h1 v-if="!pokemonCorrecto">porfavor espere..........</h1>
  <div v-else>
    <h1>Selecciona el Pokemon correcto</h1>

    <PokemonImagenVue :idPokemon="pokemonCorrecto.id" :mostrarPokemon="mostrar" />
   <div v-show="!ganador">
        <PokemonOpcionesVue :pokemons="arreglo" 
    @seleccionPokemon="revisarRespuesta($event)" />
   </div>
   
   <div>
      <h2 v-show="!ganador">Felicidades, has ganado</h2>
      <h2 v-show="ganador">Lo siento, has perdido</h2>
   </div>

  </div>
</template>

<script>
import PokemonImagenVue from "../components/PokemonImagen.vue";
import PokemonOpcionesVue from "../components/PokemonOpciones.vue";
import obtenerPokemonsFachada from "../clientes/clientePokemonApi.js";

export default {
  data() {
    return {
      arreglo: [],
      pokemonCorrecto: null,
      mostrar: false,
      ganador: false
    };
  },
  mounted() {
    this.cargaInicial();
  },
  components: {
    PokemonImagenVue,
    PokemonOpcionesVue,
  },

  methods: {
    async cargaInicial() {
      const vectorInicial = await obtenerPokemonsFachada(4);
      this.arreglo = vectorInicial;

      const indice = Math.floor(Math.random() * this.arreglo.length);
      this.pokemonCorrecto = this.arreglo[indice];
    },

    revisarRespuesta(dato){
      console.log("se emitio un evento desde el componente hijo");
      console.log(dato);
      

      if(dato.ident === this.pokemonCorrecto.id){
        this.mostrar = true;
        this.ganador = true;
      
    }else{
      this.mostrar = false;
      this.ganador = true;
    }
    }
  },
};
</script>

<style>
</style>