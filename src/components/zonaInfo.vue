<template>
    <div
        class="ml-10 text-green-300 font-extralight text-2xl  w-96 h-52 flex flex-col items-center  border border-pink-300">
        <h1 class=" mt-6 font-bold">Info</h1>
        <ul>
            <li>Registros devueltos: {{cuentaRecibida}}</li>
            <li>Paginas generadas: {{paginasRecibidas}}</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "zonaInfo",
    components: {

    },
    props: {
        cuentaRecibida:{type:Number},
        paginasRecibidas:{type:Number},
    },
    data() {
        return {

        }
    },

    methods: {

    }

}
</script>
