<template>
    <div>
        <button type="button" @click="activarReset"
            class="justify-center items-center text-black w-24 h-12 bg-green-300 hover:bg-rose-300 rounded mr-4">Limpiar</button>
        <button type="button" @click="activarBusqueda"
            class="justify-center items-center text-black w-24 h-12 bg-green-300  hover:bg-rose-300 rounded ">Aceptar</button>
      
    </div>
</template>

<script>
export default {
    name: "botonesPrincipales",
    components: {

    },
    data() {
        return {

        }
    },
    emits: ["pulsar","reset"],
    methods: {
        activarBusqueda() {
            this.$emit("pulsar");
        },
        activarReset() {
            this.$emit("reset");
        }
    }

}
</script>

