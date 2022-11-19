<template>
    <div class="mt-10 flex flex-wrap gap-5 justify-center ">
        <tipoFiltrosLocalizaciones class="mr-10" @tipo="filtroBusqueda" @dimension="filtroBusqueda" />
        <div
            class="rounded text-green-300 font-extralight text-2xl  w-96 h-52 flex flex-col justify-center items-center border border-pink-300">
            <h1 class="font-bold">Localizaciones</h1>
            <input v-model="resultado" type="text" class="w-80 mt-5 mb-5 text-black">
            <botonesPrincipales @pulsar="busquedaApi(resultado)" @reset="reset" />
        </div>
        <div>
            <zonaInfo :cuentaRecibida="cuenta" :paginasRecibidas="paginas" :estadoAnterior="paginacionPrev"
                :estadoSiguiente="paginacionNext" @pasarPaginaSiguiente="pasarPagina(this.next)"
                @pasarPaginaAnterior="pasarPagina(this.prev)" />
        </div>
    </div>

    <div class="flex flex-row flex-wrap justify-center mt-10">
        <ul>
            <li class="text-green-300 text-xl" v-for="datos in busquedaDatos" :key="datos.id">{{ datos.name }}</li>
        </ul>
    </div>

</template>
  
<script>
import axios from "axios";
import botonesPrincipales from "./botonesPrincipales.vue";
import zonaInfo from "./zonaInfo.vue";
import tipoFiltrosLocalizaciones from "./tipoFiltrosLocalizaciones.vue";


export default {
    name: "buscaPersonajes",
    components: {
        botonesPrincipales,
        zonaInfo,
        tipoFiltrosLocalizaciones,
      
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
            this.axiosStandard(`https://rickandmortyapi.com/api/location/?name=${resultado}`);
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
        async filtroBusqueda(query) {
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