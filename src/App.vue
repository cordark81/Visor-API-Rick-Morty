<template>
  <div class="mt-10 flex justify-center ">
    <div
      class="rounded text-green-300 font-extralight text-2xl  w-52 h-52 flex flex-col justify-center items-center border border-pink-300">
      <h1 class="font-bold">Busqueda</h1>
      <input v-model="resultado" type="text" class="w-40 mt-5 mb-5 text-black">
      <botonCrear @pulsar="busquedaApi(resultado)" />
    </div>

  </div>
  <div class="flex flex-row flex-wrap items-center">
    <fichaPersonaje v-for="datos in busquedaDatos" :key="datos.id" :imagenRecibida="datos.image"
      :nombreRecibido="datos.name" />
  </div>
</template>

<script>
import axios from "axios";
import botonCrear from "./components/botonCrear.vue";
import fichaPersonaje from "./components/fichaPersonaje.vue";

export default {
  name: "App",
  components: {
    botonCrear,
    fichaPersonaje,


  },
  data() {
    return {
      busquedaInfo: null,
      busquedaDatos: null,
      resultado: "",

    }

  },
  methods: {
    async busquedaApi(resultado) {
      try {
        const response = await axios.get(`https://rickandmortyapi.com/api/character/?name=${resultado}`);
        this.busquedaInfo = response.data.info;
        this.busquedaDatos = response.data.results;
      } catch (error) {
        console.log(error);
      }
    },

  }

}


</script>

<style lang="scss" scoped>

</style>