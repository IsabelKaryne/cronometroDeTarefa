<template>
    <Box>
      <div class="columns">
        <div class="column is-7">{{ tarefa.descricao || 'Tarefa sem descrição' }}</div>
        <div class="column">
          <meuCronometro :tempo="tarefa.duracaoEmSegundos"/>
        </div>
      </div>
    </Box>
  </template>
  

<script lang="ts">

import {defineComponent, PropType} from 'vue';
import meuCronometro from './cronometro.vue'
import iTarefa from '../interfaces/iTarefas';
import Box from './box.vue'
export default defineComponent({
    name: 'minhasTarefas',
    components:{
        meuCronometro,
        Box
    },
    props:{
        tarefa:{
            type: Object as PropType<iTarefa>,
            required: true
        }
    },
})
</script>
