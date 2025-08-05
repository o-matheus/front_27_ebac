<script setup>
const props = defineProps(['cadastrarTarefa','tarefaTemp', 'editaTarefaTemp' , 'trocarFiltro', ])
</script>

<template>
    <form @submit.prevent="props.cadastrarTarefa">
        <div class="row">
            <div class="col">
                <input :value="props.tarefaTemp" @change="props.editaTarefaTemp" class="form-control" required type="text" placeholder="Que atividade você quer lembrar?">
            </div>
            <div class="col-md-1">
                <button class="btn btn-primary" type='submit'>Adicionar</button>
            </div>
            <div class="col-md-2">
                <select @change="props.trocarFiltro" class="form-control">
                    <option value="todas">Todas</option>
                    <option value="pendentes">Pendentes</option>
                    <option value="finalizadas">Finalizadas</option>
                </select>
            </div>
        </div>
    </form>
</template>