<script setup>
import {reactive } from 'vue';


const estado = reactive({
  operacao: '+',
  valor1: '',
  valor2: '',
  resultado: '',

})


const calculo = () => {
  const { operacao, valor1, valor2, resultado } = estado;
  switch (operacao) {
    case '-':
      return  valor1 - valor2;
    case '/':
      return  valor1 / valor2;
    case '*':
      return  valor1 * valor2;
    default:
      return  valor1 + valor2;
  }
}

</script>

<template>
  <div class="container ">
    <h1 class="text-center p-3">Calculadora</h1>
    <form>
      <div class="row justify-content-center align-items-center">
        <div class="col-md-2">
          <input v-model="estado.valor1" class="form-control" type="number" placeholder="Insira um número"></input>
        </div>
        <div class="col-md-2">
          <input v-model="estado.valor2" class="form-control" type="number" placeholder="Insira um número"></input>
        </div>
        <div class="col-md-1">
          <select v-model="estado.operacao" class="form-control">
            <option value="+">+</option>
            <option value="-">-</option>
            <option value="*">*</option>
            <option value="/">/</option>
          </select>
        </div>
        <div class="col-md-2 d-flex align-items-center ">
          <p class="m-0 fs-5"><span class="me-3">=</span>{{ calculo() }}</p>
        </div>
      </div>
    </form>
  </div>
</template>

<style scoped></style>
