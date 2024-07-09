<script lang="ts">
import { defineComponent, type PropType } from 'vue';
import Cronometro from './Cronometro.vue';
import type ITarefa from '../interfaces/ITarefa.ts';

export default defineComponent({
    name: 'tarefaApp',
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    }, created() {
        console.log(this.tarefa.duracao);
    },
    components: {
        Cronometro: Cronometro
    }
})
</script>

<template>
    <div class="tarefa">
        <p class="descricao">{{ tarefa.descricao }}</p>
        <p class="categoria">{{ tarefa.categoria }}</p>
        <Cronometro class="cronometro" :tempo-em-segundos="tarefa.duracao" />
    </div>
</template>

<style scoped>
.tarefa {
    display: flex;
    gap: 10px;
    align-items: center;
    justify-content: space-between;

    background-color: var(--azul-claro);
    padding: 10px;
    border-radius: 10px;

    margin-bottom: 10px;
}

.categoria {
    background-color: var(--azul-presidente);
    padding: 10px;
    border-radius: 10px;

    width: 20%;
    min-width: 80px;
    text-align: center;

    color: aliceblue;
}

.descricao {
    width: 50%;
}

.cronometro {
    background-color: var(--azul-presidente);
    width: 20%;
    min-width: 100px;
}

@media (max-width: 425px) {
    .tarefa {
        flex-direction: column;
        justify-content: space-between;
    }

    .categoria, .cronometro, .descricao {
        width: 100%;
    }
}
</style>