<template>
    <div>
        <button type="button"  @click="activarBusqueda"
            class="justify-center items-center text-green-300 w-24 h-12 bg-red-700 rounded ">aceptar</button>

    </div>
</template>

<script>
export default {
    name: "botonCrear",
    components: {

    },
    data() {
        return {

        }
    },
    emits: ["pulsar"],
    methods: {
        activarBusqueda() {
            this.$emit("pulsar");
        }
    }

}
</script>

