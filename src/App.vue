<script lang="ts">
import { defineComponent, type PropType } from 'vue';
import Header from './components/Header.vue';
import Tarefa from './components/Tarefa.vue';
import type ITarefa from './interfaces/ITarefa';

export default defineComponent({
  name: 'appPrincipal',
  data() {
    return {
      tarefas: [] as ITarefa[]
    }
  },
  components: {
    Tarefa: Tarefa,
    Header: Header
  },
  methods: {
    adicionarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa);
      console.log(this.tarefas);
    }
  }
})

</script>

<template>
  <Header @tarefaFinalizada="adicionarTarefa" />
  <main>
    <Tarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
  </main>
</template>

<style scoped>
  main {
    min-width: 600px;
    height: 500px;
    margin: auto;

    overflow-y: auto
  }

</style>
