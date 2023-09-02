<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <meuCronometro :tempo="tempoEmSegundos" />
        <button class="button" @click="iniciar" :disabled="crononetroRodando">
            <span class="icon">
                <i class="fas fa-play"></i>
            </span>
            <span>Iniciar</span>
        </button>

        <button class="button" @click="finalizar" :disabled="!crononetroRodando">
            <span class="icon">
                <i class="fas fa-pause"></i>
            </span>
            <span>Finalizar</span>
        </button>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import meuCronometro from './cronometro.vue'
export default defineComponent({
    name: 'temporizadorDeacoes',
    emits: ['temporizadorFinalizado'],
    components:{
        meuCronometro
    },
    data(){
        return{
            tempoEmSegundos: 0,
            cronometro : 0,
            crononetroRodando: false,
        }
    },
    computed:{
        // indicando retornar uma string
        tempoDecorrido() : string{ 
            return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11,8)
        }
    },
    methods:{
        iniciar(){
            //começar a contagem
            this.crononetroRodando = true
            this.cronometro = setInterval(()=>{
                this.tempoEmSegundos+= 1
            }, 1000)
        },
        finalizar(){
            this.crononetroRodando = false
            clearInterval(this.cronometro)
            this.$emit('temporizadorFinalizado', this.tempoEmSegundos)
            this.tempoEmSegundos = 0
        },
    }
})
</script>