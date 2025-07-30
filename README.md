# Módulo 27 - VueJS

## Menu
[Aula 1 - Conheça o VueJS](#aula-1---conheça-o-vuejs)    
[Aula 2 - Integre o VueJS ](#aula-2---integre-o-vuejs)      
[Aula 3 - Faça a renderização condicional ](#aula-3---faça-a-renderização-condicional)      
[Aula 4 - Utilize eventos para manipular os dados ](#aula-4---utilize-eventos-para-manipular-os-dados)      
[Aula 5 - Aplique estilos de forma condicional ](#aula-5---aplique-estilos-de-forma-condicional)      
[Aula 6 - Trabalhe em listas ](#aula-6---trabalhe-em-listas)      
[Aula 7 - Crie componentes ](#aula-7---crie-componentes)      
[Tarefa ](#tarefa)      

## Aula 1 - Conheça o VueJS

### Objetivos
* Conhecer o VueJS
* Entender a relação com o Javascript
* Perceber suas principais vantagens

### Pontos Importantes
VueJS é um framework que vai atuar com o JavaScript criando funções reativas a depender da situação e trabalhando com templates.
SPA -> Single Page Application -> Uma tela onde o conteúdo dela é alterado / autualizado, fazendo que o usuário possa navegar sem sair da página em específico.
`npm create vue@latest` -> Comando para instalar o vue.
Depois disso vão ter algumas perguntas e opções para ver o que queremos utilizar e aplicar no projeto.
`cd vue-project` -> mudar para a pasta onde o projeto do vue foi guardado
`npm install` -> Instação dos módulos do node
`npm run dev` -> Execução Node com o scrpt dev

O Vue vai ter o html, javascript, só que a forma como vai estruturar o site vai ser usando componentes.

   

## Aula 2 - Integre o VueJS

### Objetivos
* Integrar VueJS com o HTML
* Utilizar o JavaScript para fazer interações dinâmicas

### Pontos Importantes
Nessa aula o professor foi apagando todo o arquivo exemplo pra que entedessemos melhor a estrutura do vue.
``` vue
Javascript
<script setup>

</script>
HTML
<template>
  <h1></h1>
</template>
CSS
<style scoped>

</style>
```
Podemos trabalhar com objetos, constantes, funções no {{}}. Fazendo a interpolação.
Mas vai existir uma forma correta de preencher os atributos do HTML com um elemento dinâmico do Javascript, temos que utilizar o `v-bind` para fazer a ligação dos dois.
Exemplo: 
`<img v-bind:src="imagemCarro" alt="">`
Aqui ele esta utilizando o valor da constante imagemCarro para ser a fonte da tag `img`
Existe um atalho para não ter que escrever o `v-bind` só usar os `:` antes do src
`<img :src="imagemCarro" alt="">`
O bind vai ser mais usado em atributos html ou componentes;
Tenho que estudar mais sobre `bind`!

Quando alterar atributos usamos o `bind`, quando vamos alterar um valor de uma tag html usamos `{{}}`
## Aula 3 - Faça a renderização condicional

### Objetivos
* realizar a renderização condicional de elementos com base em condições em VueJS;
* praticar a utilização de diretivas para controlar a renderização de conteúdo com base em condições específicas.
### Pontos Importantes
A renderização condicional vai seguir diretivas usando `v-algo`.
`v-if` -> Só vai ser renderizado se a condição for atendida.
`v-else-if` e `v-else` -> Com essas diretivas outras condições vão sendo abordadas para definir se o elemento vai ser ou não renderizado. 
`v-show` -> Vai fazer a alteração do display do conteúdo, renderizando, mas não necessariamente mostrando. 

Tenho que ler mais sobre Reatividade do vueJS, ajuda a construir elementos dinâmicos.

## Aula 4 - Utilize eventos para manipular os dados

### Objetivos
* Utilizar eventos para manipular dados
* Compreender mais sobre a reatividade do vueJS

### Pontos Importantes
Da mesma forma que não podemos usar a escrita padrão do JavaScript para interagir com elementos do DOM no vueJS, para fazer o acompanhamento de eventos existe uma maneira própria do Framework, é o que vamos aprender na aula de hoje. 
Reatividade é a capacidade de colocar um valor atualizado a partir de um evento específico.

``` vue 
<script setup>
const estado = reactive({
  contador: 0,
})

function incrementar() {
  estado.contador ++
}
</script>

<template>
  <button @click="incrementar"  type="button">+</button>
</template>
```

Essa é a estrutura básica para construção da reatividade com vueJS, temos que criar uma variável para chamar a função reactive e dentro dela nós vamos colocar os elementos que podem ter uma atualização dinâmica dentro do código no caso o professor criou um objeto. Para que possamos acompanhar algum evento dentro do vue vamos usar o `@` como usamos os `:` para fazer a diretivas da reatividade.
`ref` e `reactive`

v-model é bem bom, depois estudar mais sobre. 

## Aula 5 - Aplique estilos de forma condicional

### Objetivos
* Como aplicar estilos de forma condicional

### Pontos Importantes
Essa estilização condicional vai ser por meio de alterações da classe que vai ter um estilo definido.
O processo para fazer a estilização vai envolver usar o bind para fazer uma estrutura de condiconal dentro do atributo classe e nesse em específico utilizamos um operador ternário para fazer a condição de forma mais reduzida. 
`<input :class="{ invalido: !validarValor() }"`

* Operador ternário


## Aula 6 - Trabalhe em listas

### Objetivos
* Manipular listas de elementos e facilitar a renderização

### Pontos Importantes
Renderização de arrays com o vueJS. Para renderizar os valores nós temos que usar o `v-for`.
Estrutura referência para usar no `v-for` caso eu queira mostrar todos os valores do array.
``` vue
<ul>
  <li v-for="value in myObject">
    {{ value }}
  </li>
</ul>
```

Não precisa necessariamente ser uma tag li para utilizar o v-for, pode ser usado também com outras tags. Como títulos, imagens...

Lib boa para icons - Lucide icons
## Aula 7 - Crie componentes

### Objetivos

### Pontos Importantes


## Tarefa