<template>
  <div>
    <div class=" d-flex justify-content-center ">
      <div class="card text-center mt-5">
        <h1 class=" mt-4">{{ tittle }}</h1>
        <input
          id="personaje"
          type="text"
          class="form-control text-center"
          v-model="personaje.nombre"
          placeholder="Ingresa el nombre de un pokémon"
          @keyup.enter="fetchPersonaje"
        /><br />
        <button
          type="button"
          class="btn bg-pink"
          @click.prevent="fetchPersonaje" 
        >
          Buscar
        </button>
        <img class="mt-2" id="poke" :src="image.front_default" alt="" />
        <h3 class="font-weight-bold">Movimientos</h3>
        <ul>
          <li v-for="(movimiento, index) in movimientos" :key="index">
            {{ movimiento.move.name }}
          </li>
        </ul>
        <h3 class="font-weight-bold">Habilidades</h3>
        <ul>
          <li v-for="(habilidad, index) in habilidades" :key="index">
            {{ habilidad.ability.name }}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "pokeguia",
  // props: {},
  data: function () {
    return {
      tittle: "PokeGuía",
      personaje: {
        nombre: "",
        movimiento: "",
        movimientos: [],
        habilidades: [],
        habilidad: "",
        sprites: {
          front_default: "",
        },
      },
    };
  },
  computed: {
    image() {
      return this.personaje.sprites;
    },
    habilidades() {
      return this.personaje.abilities;
    },
    movimientos() {
      return this.personaje.moves;
    },
  },
  // computed: {},
  methods: {
    fetchPersonaje() {
      fetch(`https://pokeapi.co/api/v2/pokemon/${this.personaje.nombre}`)
        .then((response) => response.json())
        .then((json) => {
          console.log(json);
          this.personaje = json;
        })
        .catch((error) => {
          alert("personaje no encontrado");
          console.log(error);
        });
    },
  },
  created: function () {
    this.fetchPersonaje;
  },
  mounted: function () {
    this.personaje.nombre = "pikachu";
    this.fetchPersonaje();
  },
  // components: {},
};
</script>

<style scoped>
#poke{
    width:100px;
    align-self:center;
  }
li{
  text-decoration: none;
  list-style: none;
}
.card{
  border: 0;
  width: 250px;
  background: lightgoldenrodyellow;
  padding: 1em;
  border-radius: 5%

}
h1{
  color: lightpink;
  font-family: cursive;
  font-weight: 600;
   -webkit-text-stroke-width: 1px;
  -webkit-text-stroke-color: black;
}
input{
  font-size: 12px;
}
.bg-pink{
  background-color: lightpink;
  color:indianred;
 
}
</style>