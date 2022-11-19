<template>
    <div
        class="ml-10 text-green-300 font-extralight text-2xl  w-96 h-52 flex flex-col items-center  border border-pink-300">
        <h1 class=" mt-6 font-bold">Tipos de filtros</h1>
        <div class="grid grid-cols-2 w-80 h-32 ml-16 mt-10 text-lg">
            <button type="button" @click="tipo"
                class="justify-center items-center text-black w-24 h-12 bg-green-300 hover:bg-rose-300 rounded">Tipo</button>
            <button type="button" @click="dimension"
                class="justify-center items-center text-black w-24 h-12 bg-green-300  hover:bg-rose-300 rounded">Dimensión</button>
          
        </div>
    </div>
</template>

<script>
export default {
    name: "tipoFiltrosPersonajes",
    emits:["tipo","dimension"],
    methods:{
        tipo(){
            this.$emit("tipo","https://rickandmortyapi.com/api/location/?type=");
        },
        dimension(){
            this.$emit("dimension","https://rickandmortyapi.com/api/location/?dimension=");
        }

    }

}
</script>

<style lang="scss" scoped>

</style>