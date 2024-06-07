<template>
  <h2>{{presentar}} </h2>
  <p>{{numero*numero}}</p>
  <p>{{numero}}<sup>2</sup>={{numero*numero}}</p>
  <p>{{numero}}<sup>2</sup>={{calcular }}</p>
<div>
<button v-on:click="incrementar()" >+1</button>
<button @click="disminuir( )">-1</button>
</div>
</template>

<script>
export default {

props:['titulo','num'],

  data(){
    return{
      numero: 5,

  };

},

  methods:{
    calcularCuadrado(){
      console.log('ingreso al metodo');
      return this.numero * this.numero;
    },
    calcularCuadrado2(num1 , num2){
      console.log('ingreso al metodo 2');
      return num1 * num2;

    },
    incrementar(){
      this.numero++;
    },
    disminuir(){
      this.numero--;
    }
  },
  computed:{
    //toma el dato de cache
    
    calcular(){
      console.log('ingreso a la propiedad computada');
      return this.numero * this.numero;
    },
    presentar(){
      if(this.titulo !== undefined){
        return this.titulo;
      }else{
        return 'No hay titulo';
      }
    }
  }
}
</script>

<style>

button{
  margin: 0px  10px;
  padding: 5px 15px;
  border: 1px solid white;
  border-radius: 5px;
  background-color: #1aac5b;
  color: white;
  cursor: pointer;
  
}

button:hover{
  background-color: #0f472c;
  }
</style>