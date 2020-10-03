<template>
  <div>
    <h1>PokeGuia</h1>
    <form action="">
      <label for="">Ingrese nombre personaje:</label>
      <input type="text">
      <input type="submit" value="buscar">
    </form>
  </div>
</template>

<script>
export default {
  name: "poke-component",
  // props: {},
  data: function () {
    return {
      personaje:{
        name:"",
      }
    };
  },
  // computed: {},
  methods: {
    // -- Metodos
  },
  // components: {},
};
</script>

<style scoped>
</style>