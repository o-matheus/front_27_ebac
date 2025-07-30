// JavaScript
<script setup>
import { reactive } from 'vue';

let nome = "Matheus Aguiar"
const obj = {
  nome: "Matheus",
  filmeFavorito: "Interstellar"
}

function ola() {
  return `${nome} diz olá`
}
const gostaCarro = false;
const gostaBatman = false;

const imagemCarro = "https://www.shutterstock.com/shutterstock/photos/2167524427/display_1500/stock-photo-s-o-paulospbrazil-chevrolet-opala-cc-model-ss-manufactured-by-general-2167524427.jpg"

const imagemBatman = "https://wallpapers.com/images/high/batman-pictures-mubc0otf5kml1zza.webp"


// let contador = 0

// Reatividade
const estado = reactive({
  contador: 0,
  email: "",
  saldo: 5000,
  transferindo: 0,
  nomes: ["José", "Lucas", "Matheus", "Wellzsx"],
  nomeAAdicionar: '',

})

function incrementar() {
  estado.contador++;
}

function decrementar() {
  estado.contador--;
}

// Aqui foi feito o encapsulamento da função do @keyup
function alterarEmail(i) {
  estado.email = i.target.value;
}

function mostraSaldoFuturo() {
  const { saldo, transferindo } = estado;
  return saldo - transferindo;

}

function validarValor() {
  const { saldo, transferindo } = estado;
  return saldo >= transferindo;
}

function cadastrarNome() {
  estado.nomes.push(estado.nomeAAdicionar)
}



</script>

// HTML
// Essas duas chaves ou "bigode" servem para injetar um elemento definido no JavaScript no código HTML {{}}
<template>
  <h1>{{ ola() }}</h1>
  <img v-if="gostaCarro" :src="imagemCarro" alt="">
  <img v-else-if="gostaBatman" :src="imagemBatman" alt="">
  <h2 v-else>Não gosta do Batman nem de Opala</h2>

  <br>
  <hr>

  {{ estado.contador }}

  <button @click="incrementar" type="button">+</button>
  <button @click="decrementar" type="button">-</button>

  <br>
  <hr>

  {{ estado.email }}
  <input type="email" @keyup="alterarEmail">
  <!-- Forma reduzida de fazer a função sem usar o @keyup / @change só acompanha as alterações depois que o campo não está em foco -->
  <!-- <input v-model="estado.email" type="email"> -->

  <br>
  <hr>
  Saldo: {{ estado.saldo }} <br>
  Transferindo: {{ estado.transferindo }} <br>
  Saldo depois da transferência: {{ mostraSaldoFuturo() }} <br>
  <input :class="{ invalido: !validarValor() }" v-model="estado.transferindo" type="number"
    placeholder="Quantia para transferir">

  <br>
  <hr>

  <ul>
    <li v-for="nome in estado.nomes">
      {{ nome }}
    </li>
  </ul>
  {{ estado.nomeAAdicionar }}
  <input v-model="estado.nomeAAdicionar" type="text" placeholder="Digite um novo nome">
  <button @click="cadastrarNome" type="button">Cadastrar nome</button>
</template>

// CSS
<style scoped>
.invalido {
  border-color: red;
  outline-color: red;
}
</style>
