<template>
   <div class="border border-pink-300 flex w-96 h-64 rounded-3xl overflow-hidden shadow-lg mt-10 ml-10">
        <img class="w-48 h-64" :src="imagenRecibida" alt="Foto">
        <div class="border border-pink-300 w-full bg-rose-300">
            <div class="pt-24 font-bold text-xl text-center mb-2 text-violet-800 mt-3"> {{ nombreRecibido }} </div>
            
        </div>
    </div>
</template>

<script>
    export default {
        name: "fichaPersonaje",
    components: {

    },
    props:{
        imagenRecibida:{type:String},
        nombreRecibido:{type:String}
    },
    data() {
        return {

        }
    },
    
    methods: {
       
    }
        
    }
</script>

