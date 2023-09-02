<!-- componente vue dividido em até três porções: Template(html), script(javascript/typescript), style(estilo do componente) -->

<template>
    <header>
        <h1>
            <img src="../assets/relogio.png" alt="logo do alura tracker">
        </h1>
        <button class="button" @click="alterarfundo">
            {{ textoBotao }}
        </button>
    </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'barraLateral',
    emits:['aoTemaAlterado'],
    data(){
        return{
            escuroAtivo:false
        }
    },
    computed:{
        textoBotao(){
            if(this.escuroAtivo){
                return 'Desativar modo escuro'
            }else{
                return 'Ativa modo escuro'
            }
        }
    },
    methods:{
        alterarfundo(){
            this.escuroAtivo = !this.escuroAtivo
            this.$emit('aoTemaAlterado', this.escuroAtivo)
        }
    }
})
</script>

<style scoped>
/*todo o estilo do componente*/
header {
    padding: 1rem;
    background: #E3CCAE;
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