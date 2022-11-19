<template>
    <div>
        <button type="button" @click="activarReset"
            class="justify-center items-center text-green-300 w-24 h-12 bg-red-700 rounded mr-4">Limpiar</button>
        <button type="button" @click="activarBusqueda"
            class="justify-center items-center text-green-300 w-24 h-12 bg-red-700 rounded ">Aceptar</button>
      
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

