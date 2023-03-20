<script setup>
import {reactive} from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';
import Resultado from './components/Resultado.vue';

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
    <Cabecalho />
    <Formulario :numero-a="estado.numeroA" :numero-b="estado.numeroB" :pega-numero-a="evento => estado.numeroA = evento.target.value" :pega-numero-b="evento => estado.numeroB = evento.target.value" :muda-operacao="evento => estado.operacoes = evento.target.value" />
    <Resultado :condicao="estado.numeroA === '' || estado.numeroB === ''" :resultado-operacao="selecionaOperacao()"/>
  </div>
</template>
