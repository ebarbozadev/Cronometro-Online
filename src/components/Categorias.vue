<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'categoriasToDoList',
    emits: ['categoriaSelecionada'],
    data() {
        return {
            categorias: ['Trabalho', 'Pessoal', 'Acadêmico'],
            selecionado: Boolean
        }
    },
    methods: {
        pegaCategoria(evento: Event) {
            const target = evento.target as HTMLSelectElement;
            this.$emit('categoriaSelecionada', target.value);
        }
    }
})
</script>

<template>
    <select @change="pegaCategoria" name="categoria" id="categoria">
        <option value="">Selecione</option>
        <option v-for="categoria in categorias" v-bind:key="categoria" v-bind:value="categoria">
            {{ categoria }}
        </option>
    </select>
</template>

<style scoped>
select {
    outline: none;
    border: none;

    border-radius: 0px 10px 10px 0px;

    padding: 9px 0px 9px 5px;
    width: 100px;
}
</style>