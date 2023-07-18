<template>
  <header>
    <h1 class="has-text-centered">
      <img src="../assets/logo.png" alt="Logo">
    </h1>
    <button class="button" @click="alterarTema">
      {{ textoBotao }}
    </button>
  </header>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: 'BarraLateral',
  emits: ['TemaAlterado'],
  computed :{
    textoBotao(): string {
      if (this.modoEscuroAtivo) {
        return 'Desativar modo escuto';
      }
      return 'Ativar modo escuro'
    }
  },
  data() {
    return {
      modoEscuroAtivo: false
    }
  },
  methods: {
    alterarTema() {
      this.modoEscuroAtivo = !this.modoEscuroAtivo
      this.$emit('TemaAlterado', this.modoEscuroAtivo)
    },
  }
})
</script>

<style scoped>
  header {
    padding: 1rem;
    background: #0d3b66;
    width: 100%;
    height: 100vh;
    text-align: center;
  }
  @media only screen and (max-width: 768px) {
    header {
      padding: 2.5rem;
      height: auto;
    }
  }
</style>