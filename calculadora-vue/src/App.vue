<script setup>
import { reactive } from "vue";

const calcular = reactive({
  num1: 0,
  num2: 0,
  valorTemp: '',
  opcao: 'opcao',
});

const select = () => {
  const { opcao } = calcular;

  switch (opcao) {
    case 'soma':
      somarValores();
      break;
    case 'subtrair':
      subtrairValores();
      break;
    case 'multiplicar':
      multiplicarValores();
      break;
    case 'dividir':
      dividirValores();
      break;
    default:
      calcular.valorTemp = 'Operação inválida';
  }
};

const somarValores = () => {
  const valor1 = parseFloat(calcular.num1);
  const valor2 = parseFloat(calcular.num2);
  calcular.valorTemp = valor1 + valor2;
};

const subtrairValores = () => {
  const valor1 = parseFloat(calcular.num1);
  const valor2 = parseFloat(calcular.num2);
  calcular.valorTemp = valor1 - valor2;
};

const multiplicarValores = () => {
  const valor1 = parseFloat(calcular.num1);
  const valor2 = parseFloat(calcular.num2);
  calcular.valorTemp = valor1 * valor2;
};

const dividirValores = () => {
  const valor1 = parseFloat(calcular.num1);
  const valor2 = parseFloat(calcular.num2);
  calcular.valorTemp = valor2 !== 0 ? valor1 / valor2 : "Divisão por zero!";
};

</script>

<template>
  <div class="container bg-secondary rounded-3 col-3 p-5">
    <h1>Calculadora usando VUE</h1>
    <input type="number" v-model.number="calcular.num1" placeholder="Número 1">
    <input type="number" v-model.number="calcular.num2" placeholder="Número 2">
    <select v-model="calcular.opcao" @change="select" class="form-control mt-5">
      <option disabled selected value="opcao">Opções:</option>
      <option value="soma">Somar</option>
      <option value="subtrair">Subtrair</option>
      <option value="multiplicar">Multiplicar</option>
      <option value="dividir">Dividir</option>
    </select>
    <p class="text-light mt-3">{{ calcular.valorTemp }}</p>
  </div>
</template>

<style scoped>
</style>
