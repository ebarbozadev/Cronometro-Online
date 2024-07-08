<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'botaoApp',
    emits: ['clicado'],
    props: {
        desabilitado: {type: Boolean},
        texto: {type: String, required: true}
    },
    methods: {
        clicado() : void {
            this.$emit('clicado');
        }
    }
})


</script>

<template>
    <button @click="clicado" :disablet="desabilitado">
        {{ texto }}
    </button>
</template>

<style scoped>
button {
    outline: none;
    border: none;

    border-radius: 10px;

    height: 35px;
    width: 100px;

    cursor: pointer;
}
</style>