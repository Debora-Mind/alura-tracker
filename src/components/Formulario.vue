<template>
  <div class="box formulario">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tag">
        <input
            type="text"
            class="input"
            placeholder="Qual tarefa você deseja iniciar?"
            v-model="descricao"
        />
      </div>
      <div class="column">
        <Temporizador @temporizadorFinalizado="finalizarTarefa"/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
  import { defineComponent } from "vue";
  import Temporizador from "@/components/Temporizador.vue";

  export default defineComponent({
    // eslint-disable-next-line vue/multi-word-component-names
    name: "Formulário",
    emits: ['salvarTarefa'],
    components: {Temporizador},
    data () {
      return {
        descricao: ''
      }
    },
    methods: {
      finalizarTarefa(tempoDecorrido: number): void {
        this.$emit('salvarTarefa', {
          duracaoEmSegundos: tempoDecorrido,
          descricao: this.descricao
        })
        this.descricao = ''
      }
    }
  })
</script>

<style>
  .formulario {
    color: var(--texto-primario);
    background: var(--bg-primario);
  }
</style>