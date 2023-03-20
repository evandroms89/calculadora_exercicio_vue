<script setup>
import {reactive} from 'vue';

const estado = reactive({
  operacoes: '',
  numeroA: '',
  numeroB: '',
})

const adicao = () => {
  return parseFloat(estado.numeroA) + parseFloat(estado.numeroB);

  
}

const subtracao = () => {
  return parseFloat(estado.numeroA) - parseFloat(estado.numeroB);
}

const multiplicacao = () => {
  return parseFloat(estado.numeroA) * parseFloat(estado.numeroB);
}

const divisao = () => {
  return parseFloat(estado.numeroA) / parseFloat(estado.numeroB);
}

const selecionaOperacao = () => {
  const { operacoes } = estado;

  switch (operacoes) {
    case 'subtracao':
      return subtracao();
    case 'multiplicacao':
      return multiplicacao();
    case 'divisao':
      return divisao();
    default:
      return adicao();
  }

}

</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-light text-center">
      <h1>Calculadora</h1>
    </header>
    <form class="text-center mt-5">
      <div class="row d-flex justify-content-center">
        <div class="col-md-2">
          <input :value="estado.numeroA" @keyup="evento => estado.numeroA = evento.target.value" type="text" placeholder="Insira um número" class="form-control">
        </div>
        <div class="col-md-1">
          <select @change="evento => estado.operacoes = evento.target.value" class="form-select">
            <option value="adicao">+</option>
            <option value="subtracao">-</option>
            <option value="multiplicacao">x</option>
            <option value="divisao">/</option>
          </select>
        </div>
        <div class="col-md-2">
          <input :value="estado.numeroB" @keyup="evento => estado.numeroB = evento.target.value" type="text" placeholder="Insira um número" class="form-control">
        </div>
      </div>
    </form>
    <div class="col-md-12 mt-5 text-center">
      <h3 v-if="estado.numeroA === '' || estado.numeroB === ''"></h3>
      <h3 v-else>O resultado é {{ selecionaOperacao() }}</h3>
    </div>

  </div>
</template>

<style scoped>
</style>
