<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <Cronometro :tempoEmSegundos="tempoEmSegundos" />
    <botao @clicado="iniciar" icone="fas fa-play" texto="Play" :desabilitado="cronometroRodando" />
    <botao @clicado="finalizar" icone="fas fa-stop" texto="Stop" :desabilitado="!cronometroRodando" />
  </div>
</template>

<script>
import Cronometro from "@/components/Cronometro";
import Botao from "@/components/Botao.vue";

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Temporizador",
  components: {Cronometro, Botao},
  emits: ['temporizadorFinalizado'],
  data() {
    return {
      tempoEmSegundos: 0,
      cronometro: 0,
      cronometroRodando: false,
    }
  },
  methods: {
    iniciar(){
      this.cronometroRodando = true;
      this.cronometro = setInterval(() => {
        this.tempoEmSegundos += 1
      }, 1000)
    },
    finalizar(){
      this.cronometroRodando = false;
      clearInterval(this.cronometro);
      this.$emit('temporizadorFinalizado', this.tempoEmSegundos);
      this.tempoEmSegundos = 0;
    }
  }
}
</script>
