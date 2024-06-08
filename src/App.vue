<template>
  <img alt="Vue logo" src="./assets/logo.png" />
    <contador titulo="Estudiante" :num="1"/>
    <contador titulo="Profesor" />
    <contador :num= "calcularValor()"/>


</template>

<script>
import contador from "./components/Contador.vue";

export default {
  name: "App",
  components: {
    contador,
  },

  methods:{
    calcularValor(){
      return 10 + 2;
    }
  }

};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
