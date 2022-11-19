<template>
  <div class="mt-10 flex flex-wrap gap-5 justify-center ">
    <div
      class="rounded text-green-300 font-extralight text-2xl  w-52 h-52 flex flex-col justify-center items-center border border-pink-300">
      <h1 class="font-bold">Busqueda</h1>
      <input v-model="resultado" type="text" class="w-40 mt-5 mb-5 text-black">
      <botonCrear @pulsar="busquedaApi(resultado)" />
    </div>
    <div>
      <zonaInfo :cuentaRecibida="cuenta" :paginasRecibidas="paginas" />
    </div>
  </div>
  <div class="flex flex-row justify-center gap-4 mt-10">
    <botonAnterior @pasaPagina="pasarPagina(this.prev)" :estado="paginacionPrev" />
    <botonSiguiente @pasaPagina="pasarPagina(this.next)" :estado="paginacionNext" />

  </div>
  <div class="flex flex-row flex-wrap justify-center items-center">
    <fichaPersonaje v-for="datos in busquedaDatos" :key="datos.id" :imagenRecibida="datos.image"
      :nombreRecibido="datos.name" />
  </div>

</template>

<script>
import axios from "axios";
import botonCrear from "./components/botonCrear.vue";
import fichaPersonaje from "./components/fichaPersonaje.vue";
import zonaInfo from "./components/zonaInfo.vue";
import botonSiguiente from "./components/botonSiguiente.vue";
import botonAnterior from "./components/botonAnterior.vue";

export default {
  name: "App",
  components: {
    botonCrear,
    fichaPersonaje,
    zonaInfo,
    botonSiguiente,
    botonAnterior,
  },
  data() {
    return {
      busquedaDatos: null,
      resultado: "",
      cuenta: 0,
      paginas: 0,
      next: null,
      prev: null,
    }

  },
  methods: {
    async busquedaApi(resultado) {
      try {
        const response = await axios.get(`https://rickandmortyapi.com/api/character/?name=${resultado}`);
        this.busquedaDatos = response.data.results;
        this.cuenta = response.data.info.count;
        this.paginas = response.data.info.pages;
        this.next = response.data.info.next;
        this.prev = response.data.info.prev;

      } catch (error) {
        this.next = null;
        this.prev = null;
        console.log(error);
      }
    },
    async pasarPagina(url) {
      try {
        const response = await axios.get(url);
        this.busquedaDatos = response.data.results;
        this.cuenta = response.data.info.count;
        this.paginas = response.data.info.pages;
        this.next = response.data.info.next;
        this.prev = response.data.info.prev;

      } catch (error) {
        this.next = null;
        this.prev = null;
        console.log(error);
      }
    }



  },
  computed: {
    paginacionNext() {
      return (this.next == null);
    }

    , paginacionPrev() {
      return (this.prev == null);

    }
  }
}


</script>

<style lang="scss" scoped>

</style>