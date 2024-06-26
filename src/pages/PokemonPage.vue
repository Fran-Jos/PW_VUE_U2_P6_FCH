<template>
  <div class="container">
    <div class="score">
      <h2>Intentos:{{ intentos }}</h2>
      <h2>Puntaje:{{ puntos }}</h2>
    </div>
    <h1>Seleccionar el pokemon Correcto</h1>
    <PokemonImagen :idPokemon="pokemonCorrecto.id" :mostrarPokemon="mostrar" />
    <PokemonOpciones
      :pokemons="arreglo"
      @SeleccionPokemon="revisarRespuesta($event)"
    />

    <p v-show="pokemonC">Felicidades has ganado el juego</p>
    <p v-show="!pokemonC && sigaIntentado">
      Pokemon incorrecto, Siga intentando
    </p>
  </div>
</template>

<script>
import PokemonImagen from "../components/PokemonImagen.vue";
import PokemonOpciones from "../components/PokemonOpciones.vue";
import obtenerPokemonsFachada from "../clientes/clientePokemonAPI";

export default {
  components: {
    PokemonImagen,
    PokemonOpciones,
  },
  data() {
    return {
      arreglo: [],
      mostrar: false,
      pokemonCorrecto: "",
      pokemonC: false,
      sigaIntentado: false,
      intentos: 0,
      puntos: 0,
    };
  },
  methods: {
    async cargaInicial() {
      const vectorInicial = await obtenerPokemonsFachada(7);
      this.arreglo = vectorInicial;
      const indice = Math.floor(Math.random() * 7 + 1);
      this.pokemonCorrecto = this.arreglo[indice];
    },
    revisarRespuesta(data) {
      this.intentos++;
      console.log("Se emitio un evento hijo");
      this.mostrar = true;
      if (data.ident == this.pokemonCorrecto.id) {
        this.mostrar = true;
        console.log("Respuesta correcta")
        this.pokemonC = true;

        switch(this.intentos){
          case 1:
            this.puntos +=10;
            break;
          case 2:
            this.puntos +=8;
            break;
          case 3:
            this.puntos +=5;
            break;
          case 4:
            this.puntos +=3;
            break;
          case 5:
            this.puntos +=2;
            break;
          case 6:
            this.puntos +=1;
            break;
          default:
            this.puntos +=0;



        }

      } else {
        this.mostrar = false;
        console.log("Respuesta incorrrecta")
        this.pokemonC = false;
        this.sigaIntentado = true;
      }
    },
  },

  mounted() {
    this.cargaInicial();
  },
};
</script>

<style>
.score{
  display: flex;
  flex-direction: row;
  justify-content: center;
  text-align: center;
}
h2{
  display: flex;
  justify-content: center;
  margin-left: 20px;
  
}
</style>