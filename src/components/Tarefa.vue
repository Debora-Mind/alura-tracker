<template>
  <Box>
    <div class="columns">
      <div class="column is-7">
        {{ tarefa.descricao || 'Tarefa sem descrição'}}
      </div>
      <div class="column">
        <Cronometro :tempo-em-segundos="tarefa.duracaoEmSegundos"/>
      </div>
    </div>
  </Box>
</template>

<script lang="ts">
import {defineComponent, PropType} from "vue";
import Cronometro from "@/components/Cronometro.vue";
import ITarefa from "@/Interfaces/ITarefa";
import Box from "@/components/Box.vue";

export default defineComponent({
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Tarefa",
  components: {Box, Cronometro},
  props: {
    tarefa: {
      type: Object as PropType<ITarefa>,
      required: true
    }
  },
})
</script>
