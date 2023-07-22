<template>
    <section>
        <strong>
            {{ tempoDecorrido }}
        </strong>
    </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'cronometroFormatado',
    props:{
        tempo:{
            type: Number,
            default: 0
        }
    },
    computed:{
        // indicando retornar uma string
        tempoDecorrido() : string{ 
            return new Date(this.tempo * 1000).toISOString().substr(11,8)
        }
    },
})
</script>

<!-- toISOString().substr(11,8) -->
