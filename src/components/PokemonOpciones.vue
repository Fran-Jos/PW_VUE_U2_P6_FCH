<template>
  <div class="opcionesContainer">
    <ul>
      <li>1</li>
      <li>2</li>
      <li>3</li>
      <li>4</li>
    </ul>
  </div>
</template>

<script>
export default {
  components: {},
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