<template>
  <div id="app">
    <pokeguia></pokeguia>
  </div>
</template>

<script>
import PokeGuiaComponent from "./components/Pokeguia.vue";

  export default {
    data() {
      return {
        message: 'Hola en vue',
      };
    },
    components:{
      "pokeguia": PokeGuiaComponent,
    }
  }
</script>

<style scoped>
  
</style>