<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="descricao">
            </div>
            <div class="column">
                <temporizadorDeAcoes @temporizadorFinalizado="finalizarTarefa" />
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import temporizadorDeAcoes from './temporizador.vue'

export default defineComponent({
    name: "meuFormulario",
    emits: ['aoSalvarTarefa'],
    components: {
        temporizadorDeAcoes,
    },
    data () {
    return {
      descricao: ''
    }
  },
  methods: {
    finalizarTarefa (tempoDecorrido: number) : void {
      this.$emit('aoSalvarTarefa', {
        duracaoEmSegundos: tempoDecorrido,
        descricao: this.descricao
      })
      this.descricao = ''
    }
  }
})
</script>

<style>
.formulario{
  background-color: var(--bg-primario);
  color: var(--texto-primario);
}
</style>
