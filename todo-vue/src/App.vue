<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';
import ListaDeTarefas from './components/ListaDeTarefas.vue';



const estado = reactive({
  filtro: 'todas',
  tarefaTemp: '',
  tarefas: [
    {
      titulo: 'Estudar ES6',
      finalizada: false,
    },
    {
      titulo: 'Estudar SASS',
      finalizada: false,
    },
    {
      titulo: 'Lavar roupa',
      finalizada: true,
    },
  ],
})

function cadastrarTarefa() {
  const atividadeTemp = {
    titulo: estado.tarefaTemp,
    finalizada: false,
  }
  estado.tarefas.push(atividadeTemp);
  estado.tarefaTemp = '';
}

const getTarefasPendentes = () => {
  return estado.tarefas.filter(tarefa => !tarefa.finalizada)
}
const getTarefasFinalizadas = () => {
  return estado.tarefas.filter(tarefa => tarefa.finalizada)
}

const getTarefasFiltradas = () => {
  const { filtro } = estado;

  switch (filtro) {
    case 'pendentes':
      return getTarefasPendentes();
    case 'finalizadas':
      return getTarefasFinalizadas();
    default:
      return estado.tarefas;
  }
}
</script>

<template>
  <div class="container">
    <Cabecalho :tarefas-pendentes="getTarefasPendentes().length" />
    <Formulario :cadastrar-tarefa="cadastrarTarefa" :tarefa-temp="estado.tarefaTemp" :edita-tarefa-temp="evento => estado.tarefaTemp = evento.target.value" :trocar-filtro="evento => estado.filtro = evento.target.value"/>
    <ListaDeTarefas :quantidade-tarefas="getTarefasPendentes().length" :tarefas="getTarefasFiltradas()" />
    {{ possuiTarefas }}
  </div>
</template>

