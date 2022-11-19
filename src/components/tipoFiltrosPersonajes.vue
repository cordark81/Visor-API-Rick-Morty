<template>
    <div
        class="ml-10 text-green-300 font-extralight text-2xl  w-96 h-52 flex flex-col items-center  border border-pink-300">
        <h1 class=" mt-6 font-bold">Tipos de filtros</h1>
        <div class="grid grid-cols-2 w-80 h-32 ml-16 mt-5">
            <button type="button" @click="vivos"
                class="justify-center items-center text-black w-24 h-12 bg-green-300 hover:bg-rose-300 rounded">Vivos</button>
            <button type="button" @click="muertos"
                class="justify-center items-center text-black w-24 h-12 bg-green-300  hover:bg-rose-300 rounded">Muertos</button>
            <button type="button" @click="species"
                class="justify-center items-center text-black w-24 h-12 bg-green-300  hover:bg-rose-300 rounded">Especies</button>
            <button type="button" @click="genero"
                class="justify-center items-center text-black w-24 h-12 bg-green-300  hover:bg-rose-300 rounded">Genero</button>
        </div>
    </div>
</template>

<script>
export default {
    name: "tipoFiltrosPersonajes",
    emits:["vivos","muertos","species","genero"],
    methods:{
        vivos(){
            this.$emit("vivos","&status=alive");
        },
        muertos(){
            this.$emit("muertos","&status=dead");
        },
        species(){
            this.$emit("species","https://rickandmortyapi.com/api/character/?species=");
        },
        genero(){
            this.$emit("genero","https://rickandmortyapi.com/api/character/?gender=");
        }

    }

}
</script>

<style lang="scss" scoped>

</style>