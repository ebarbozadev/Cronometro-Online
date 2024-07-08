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
</style>