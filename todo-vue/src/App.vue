<script setup>
import { reactive } from 'vue';

const estado = reactive({
  filtro: 'todas',
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
  adicionarTarefas: [
    {
      titulo: '',
      finalizada: false,
    }
  ]

})

function cadastrarTarefa() {
  estado.tarefas.push(estado.adicionarTarefas);
  estado.adicionarTarefas = "";
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
    <header class="p-5 mt-4 mb-4 bg-light rounded-3">
      <h1>Minhas tarefas</h1>
      <p>Você possui {{ getTarefasPendentes().length }} tarefas.</p>
    </header>
    <form @submit.prevent="cadastrarTarefa">
      <div class="row">
        <div class="col">
          <input required v-model="estado.adicionarTarefas.titulo" type="text" placeholder="Digite a descrição da tarefa."
            class="form-control">
        </div>
        <div class="col-md-1">
          <button type="submit" class="btn btn-primary">Cadastrar</button>
        </div>
        <div class="col-md-2">
          <select @change="evento => estado.filtro = evento.target.value" class="form-control">
            <option value="todas">Todas</option>
            <option value="pendentes">Pendentes</option>
            <option value="finalizadas">Finalizadas</option>
          </select>
        </div>
      </div>
    </form>
    <ul class="list-group mt-4">
      <li class="list-group-item" v-for="tarefa in getTarefasFiltradas()">
        <input v-model="tarefa.finalizada" :id="tarefa.titulo" type="checkbox">
        <label :class="{ done: tarefa.finalizada == true }" class="ms-3" :for="tarefa.título">
          {{ tarefa.titulo }}
        </label>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.done {
  text-decoration: line-through;
}
</style>
