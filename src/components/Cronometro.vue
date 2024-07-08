<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'cronometroToDoList',
    props: {
        tempoEmSegundos: { type: Number, default: 0, required: true }
    },
    computed: {
        tempoDecorrido(): string {
            return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11, 8);
        }
    }
})

</script>

<template>
    <div>
        <strong style="color: white">
            {{ tempoDecorrido }}
        </strong>
    </div>
</template>

<style scoped>
div {
    display: flex;
    align-items: center;
    justify-content: center;

    border: none;
    background-color: var(--azul-claro);
    border-radius: 10px;

    padding-top: 3px;
    height: 35px;
    width: 100px;
}
</style>