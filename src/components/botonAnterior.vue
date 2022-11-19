<template>
    <div class="flex">
        <button type="button" @click="pasarPagina"
            class="text-black w-24 h-12 bg-green-300 rounded " :disabled="estado">Anterior</button>

    </div>
</template>

<script>
export default {
    name:"botonAnterior",
    props:{
        estado:{type:Boolean,default:"true"},
    },
    methods:{
        pasarPagina(){
            this.$emit("pasaPagina");
            console.log("pasando pagina");
        }
    }

}
</script>

<style lang="scss" scoped>

</style>