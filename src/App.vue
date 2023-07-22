<template>
  <main class="columns is-gapless is-multiline"> <!--Essa classe indica que será criado muitas colunas e o espaçamento dessas colunas não existe(is-gapless) e pode permitir múltiplas linhas (is-multiline)-->
    <!-- Aqui terá a barra lateral  -->
    <div class="column is-one-quarter">
      <barraLateral/> <!--Criar um componente-->
    </div>
    <!-- Vai representar toda a parte da direita com o formulário no topo e as listas de tarefa embaixo -->
    <div class="column is-three-quarter">
      <meuFormulario/>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import barraLateral from './components/barraLateral.vue'
import meuFormulario from './components/formulario.vue'

export default defineComponent({
  name: 'App',
  components:{
    barraLateral,
    meuFormulario
  }
});
</script>

<style>

</style>
