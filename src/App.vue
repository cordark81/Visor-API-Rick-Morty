<template>
  <div>
    <div class="flex justify-center mt-5">
      <button @click="conmutador(cambio)" class="text-black w-24 h-12 bg-green-300 hover:bg-rose-300 rounded">Cambiar
        busqueda</button>
    </div>
    <div v-show="buscaLocalizaciones">
      <buscaLocalizaciones />
    </div>
    <div v-show="buscaPersonajes">
      <buscaPersonajes />
    </div>

  </div>
</template>

<script>
import buscaPersonajes from './components/buscaPersonajes.vue';
import buscaLocalizaciones from './components/buscaLocalizaciones.vue';
export default {
  name: "app",
  data() {
    return {
      buscaPersonajes: true,
      buscaLocalizaciones: false,
    }
  },
  components: {
    buscaPersonajes,
    buscaLocalizaciones,
  },
  methods: {
    conmutador(estado) {
      this.buscaPersonajes = estado;
      this.buscaLocalizaciones = !estado;
    }
  },
  computed: {
    cambio() {
      return this.buscaPersonajes == true ? false : true;
    }

  }
}

</script>

<style lang="scss" scoped>

</style>