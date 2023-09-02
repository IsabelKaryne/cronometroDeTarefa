<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': escuroAtivo }"> <!--Essa classe indica que será criado muitas colunas e o espaçamento dessas colunas não existe(is-gapless) e pode permitir múltiplas linhas (is-multiline)-->
    <!-- Aqui terá a barra lateral  -->
    <div class="column is-one-quarter">
      <barraLateral @aoTemaAlterado="trocarTema"/> <!--Criar um componente-->
    </div>
    <!-- Vai representar toda a parte da direita com o formulário no topo e as listas de tarefa embaixo -->
    <div class="column is-three-quarter conteudo">
      <meuFormulario @aoSalvarTarefa="salvarTarefa"/>
      <div class="listas">
        <minhasTarefas v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
      </div>
      <Box v-if="listaVazia">
        Você não está muito produtivo hoje :(
      </Box>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import barraLateral from './components/barraLateral.vue'
import meuFormulario from './components/formulario.vue'
import minhasTarefas from './components/tarefas.vue'
import iTarefa from './interfaces/iTarefas'
import Box from './components/box.vue'

export default defineComponent({
  name: 'App',
  components:{
    barraLateral,
    meuFormulario,
    minhasTarefas,
    Box
  },
  data(){
    return {
      tarefas: [] as iTarefa[],
      escuroAtivo: false
    }
  },
  computed:{
    listaVazia (): boolean{
      return this.tarefas.length === 0
    }
  },
  methods:{
    salvarTarefa(tarefa: iTarefa){
      this.tarefas.push(tarefa)
    },
    trocarTema (escuroAtivo : boolean){
      this.escuroAtivo = escuroAtivo
    }
  }
});

</script>

<style>
  .listas{
    padding: 1.25rem;
  }

  main{
    --bg-primario: #fff;
    --texto-primario: #000;
  }

  main.modo-escuro{
    --bg-primario: #2B2D42;
    --texto-primario: #dddd;
  }

  .conteudo{
    background-color: var(--bg-primario);
  }
</style>