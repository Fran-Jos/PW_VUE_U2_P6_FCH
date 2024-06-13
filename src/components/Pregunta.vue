<template>
  <img v-if="img" :src="img" alt="No hay imagen" />
  <div class="obscuro"></div>
  <div class="pregunta-container">
    <input v-model="pregunta" type="text" placeholder="Hazme una pregunta" />
    <p>Recuerda terminar la pregunta con un signo de pregunta (?)</p>

    <div class="respuesta">
      <h2>{{ pregunta }} ?</h2>
      <h1>{{ respuesta }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      pregunta: null,
      respuesta: null,
      img: null,
    };
  },

  /* watch siempre va estar observando que hay un cambio 
en la propiedad reactiva */
  watch: {
    /*
  todo observador se tiene que crear con el mismo nombre de la propiedad reactiva
  */
    pregunta(value, oldvalue) {
      console.log({ value, oldvalue });

      if (!value.includes("?")) return;
      this.obtenerRespuesta();
    },
  },

  methods: {
    async obtenerRespuesta() {
      this.respuesta = "Pensando.......";
      const data = await fetch("https://yesno.wtf/api").then((res) =>
        res.json()
      );
      const { answer, image, forced } = data;
      console.log(answer);
      this.respuesta = answer;
      this.img = image;
      return data;
    },

    async prueba() {
      const data2 = await this.obtenerRespuesta();
    },
  },
};
</script>

<style>
img,
.obscuro {
  max-height: 100%;
  height: 100vh;
  max-width: 100%;
  width: 100vw;
  position: fixed;
  top: 0px;
  left: 0px;
}

.obscuro {
  background-color: rgba(0, 0, 0, 0.7);
  /*
  0.0 --> full transparencia
  0.5 --> semi transparente
  1.0 --> full opaco
  */
}

.pregunta-container {
  position: relative;
}

input {
  width: 560px;
  padding: 10px 15px;
  border: none;
  border-radius: 5px;
  margin-top: 200px;
  text-align: center;
}

input:focus {
  outline: none;
}

p,
h1,
h2 {
  color: white;
}

p {
  font-size: 26px;
  margin-top: 0px;
}
.respuesta {
  margin-top: 100px;
}
</style>