<template>
  <div class="mt-10 flex flex-wrap gap-5 justify-center ">
    <tipoFiltros class="mr-10" @vivos="filtro" @muertos="filtro" @species="filtroSpecie" @genero="filtroGenero" />
    <div
      class="rounded text-green-300 font-extralight text-2xl  w-96 h-52 flex flex-col justify-center items-center border border-pink-300">
      <h1 class="font-bold">Busqueda</h1>
      <input v-model="resultado" type="text" class="w-80 mt-5 mb-5 text-black">
      <botonesPrincipales @pulsar="busquedaApi(resultado)" @reset="reset" />
    </div>
    <div>
      <zonaInfo :cuentaRecibida="cuenta" :paginasRecibidas="paginas" :estadoAnterior="paginacionPrev"
        :estadoSiguiente="paginacionNext" @pasarPaginaSiguiente="pasarPagina(this.next)"
        @pasarPaginaAnterior="pasarPagina(this.prev)" />
    </div>
  </div>

  <div class="flex flex-row flex-wrap justify-center items-center">
    <fichaPersonaje v-for="datos in busquedaDatos" :key="datos.id" :imagenRecibida="datos.image"
      :nombreRecibido="datos.name" />
  </div>

</template>

<script>
import axios from "axios";
import botonesPrincipales from "./components/botonesPrincipales.vue";
import fichaPersonaje from "./components/fichaPersonaje.vue";
import zonaInfo from "./components/zonaInfo.vue";
import tipoFiltros from "./components/tipoFiltros.vue";

export default {
  name: "App",
  components: {
    botonesPrincipales,
    fichaPersonaje,
    zonaInfo,
    tipoFiltros,
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
      this.axiosStandard(`https://rickandmortyapi.com/api/character/?name=${resultado}`);
    },
    async pasarPagina(url) {
      this.axiosStandard(url);
    },
    reset() {
      this.resultado = "";
    },
    filtro(query) {
      this.resultado = `${this.resultado}${query}`;

    },
    async filtroSpecie(query) {
      this.axiosStandard(`${query}${this.resultado}`);
    },
    async filtroGenero(query) {
      this.axiosStandard(`${query}${this.resultado}`);
    },
    async axiosStandard(url) {
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