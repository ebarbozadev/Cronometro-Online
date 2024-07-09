<script lang="ts">
import { defineComponent } from 'vue';
import Categorias from './Categorias.vue';
import Botao from './Botao.vue';
import Cronometro from './Cronometro.vue';

export default defineComponent({
    name: 'formularioHeader',
    emits: ['tarefaFinalizada'],
    data() {
        return {
            tempoEmSegundos : 0,
            cronometro: 0,
            cronometroRodando: false,
            descricao: '',
            categoria: ''
        }
    },
    components: {
        Categorias: Categorias,
        Cronometro: Cronometro,
        Botao: Botao
    },
    methods: {
        iniciar () {
            this.cronometro = setInterval(() => {
                this.tempoEmSegundos += 1
            }, 1000);

            this.cronometroRodando = !this.cronometroRodando;
        },
        finalizar () {
            clearInterval(this.cronometro);
            this.cronometroRodando = !this.cronometroRodando;
            this.$emit('tarefaFinalizada', {
                duracao: this.tempoEmSegundos,
                descricao: this.descricao,
                categoria: this.categoria
            })
            this.tempoEmSegundos = 0;
            this.descricao = '';
            this.categoria = '';
        },
        categoriaSelecionada(categoria : string) {
            this.categoria = categoria;
        }
    }
})

</script>

<template>
    <div class="formulario">
        <div class="informacoes">
            <input 
                type="text"
                placeholder="Digite aqui a tarefa a ser realizada"
                v-model="descricao"
            >
            <Categorias @categoria-selecionada="categoriaSelecionada"/>
        </div>

        <div class="botoes">
            <Botao @clicado="iniciar":desabilitado="cronometroRodando" texto="Iniciar" />
            <Botao @clicado="finalizar" :desabilitado="!cronometroRodando" texto="Finalizar" />
        </div>

        <Cronometro class="cronometro" :tempo-em-segundos="tempoEmSegundos" />
    </div>
</template>

<style scoped>
input {
    outline: none;
    border: none;
    border-radius: 10px 0px 0px 10px;

    padding: 10px 0px 10px 5px;
    width: 300px;
}

.formulario {
    display: flex;
    gap: 10px;
    align-items: center;
}

.botoes {
    display: flex;
    gap: 10px;
    justify-content: space-between;
}

@media (max-width: 768px) {
    .formulario {
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }

    .botoes button {
        width: 195px;
    }

    .cronometro {
        width: 100%;
    }
}

@media (max-width: 425px) {
    .botoes {
        flex-direction: column;
    }

    .informacoes input {
        width: 200px;
    }
    
    .cronometro {
        width: 300px;
    }

    .botoes button {
        width: 300px;
    }
}
</style>