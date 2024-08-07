<script setup>
import { reactive } from 'vue';

const estado = reactive({
  number1: 0,
  number2: 0,
  operador: '+'
});

function resultado() {
  const { number1, number2, operador } = estado;
  switch (operador) {
    case '+': return number1 + number2;
    case '-': return number1 - number2;
    case '*': return number1 * number2;
    case '/': return number2 !== 0 ? number1 / number2 : 'Não é possível dividir por zero';
    default: return 0;
  }
}
</script>

<template>
  <div class="calculadora">
    <h1>Calculadora</h1>
    <div class="teclado">
      <input v-model.number="estado.number1" type="number" placeholder="Número 1" />
      <select v-model="estado.operador">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
      </select>
      <input v-model.number="estado.number2" type="number" placeholder="Número 2" />
    </div>
    <div v-if="estado.number1 !== null && estado.number2 !== null">
      <p>Resultado: {{ resultado() }}</p>
    </div>
  </div>
</template>

<style scoped>
h1 {
  font-size: 3em;
}
.calculadora {
  text-align: center;
  margin-top: 80px;
}
input, select, p {
  margin: 10px;
  padding: 5px;
  font-size: 16px;
}
</style>
