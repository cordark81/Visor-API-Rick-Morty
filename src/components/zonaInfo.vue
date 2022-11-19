<template>
    <div
        class="ml-10 text-green-300 font-extralight text-2xl  w-96 h-52 flex flex-col items-center  border border-pink-300">
        <h1 class=" mt-6 font-bold">Info</h1>
        <ul>
            <li>Registros devueltos: {{ cuentaRecibida }}</li>
            <li>Paginas generadas: {{ paginasRecibidas }}</li>
        </ul>
        <div class="flex flex-row mt-3 gap-10">
            <botonAnterior :estado=estadoAnterior @pasaPagina=pasarPaginaAnterior />
            <botonSiguiente :estado=estadoSiguiente @pasaPagina=pasarPaginaSiguiente />
        </div>

    </div>
</template>
<script>
import botonSiguiente from './botonSiguiente.vue' ;
import botonAnterior from './botonAnterior.vue';

export default {
    name: "zonaInfo",

    emits:["pasarPaginaAnterior","pasarPaginaSiguiente"],

    components: {
        botonSiguiente,
        botonAnterior,

    },
    props: {
        cuentaRecibida: { type: Number },
        paginasRecibidas: { type: Number },
        estadoAnterior: {type: Boolean},
        estadoSiguiente: {type: Boolean},
    },
    data() {
        return {

        }
    },

    methods:{
        pasarPaginaAnterior(){
            this.$emit("pasarPaginaAnterior");
            
        },
        
        pasarPaginaSiguiente(){
            this.$emit("pasarPaginaSiguiente");
                       
        }
    }

}
</script>
