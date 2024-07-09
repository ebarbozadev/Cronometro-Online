<script lang="ts">
import { defineComponent } from 'vue';
import Formulario from './Formulario.vue';

export default defineComponent({
    name: 'headerApp',
    emits: ['tarefaFinalizada'],
    components: {
        Formulario: Formulario
    }
})
</script>

<template>
    <header>
        <h1>Cronômetro Online</h1>
        <Formulario class="formulario" @tarefa-finalizada="$emit('tarefaFinalizada', $event)" />
    </header>
</template>

<style scoped>
header {
    display: flex;
    align-items: center;
    justify-content: space-between;

    background-color: var(--azul-presidente);

    padding: 0px 50px;
    height: 50px;
}

.formulario {
    width: auto;
}

@media (max-width: 1163px) {
    header {
        flex-direction: column;
        align-items: center;
        justify-content: space-evenly;
        padding: 0;
        height: 100px;
    }
}

@media (max-width: 768px) {
    header {
        height: 200px;
    }
}

@media (max-width: 425px) {
    header {
        height: 260px;
    }
}
</style>