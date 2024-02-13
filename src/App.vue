<template>
  <div id="app">
    <div class="calculator">
      <input v-model="input" type="text" disabled>
      <div class="buttons">
        <button @click="appendToInput('7')">7</button>
        <button @click="appendToInput('8')">8</button>
        <button @click="appendToInput('9')">9</button>
        <button @click="appendToInput('+')">+</button>
        <button @click="appendToInput('4')">4</button>
        <button @click="appendToInput('5')">5</button>
        <button @click="appendToInput('6')">6</button>
        <button @click="appendToInput('-')">-</button>
        <button @click="appendToInput('1')">1</button>
        <button @click="appendToInput('2')">2</button>
        <button @click="appendToInput('3')">3</button>
        <button @click="appendToInput('*')">*</button>
        <button @click="appendToInput('0')">0</button>
        <button @click="clearInput">C</button>
        <button @click="calculate">=</button>
        <button @click="appendToInput('/')">/</button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const input = ref('');

function appendToInput(value) {
  input.value += value;
}

function clearInput() {
  input.value = '';
}

function calculate() {
  try {
    input.value = eval(input.value);
  } catch (error) {
    input.value = 'Error';
  }
}
</script>

<style>
.calculator {
  border: 1px solid #ccc;
  padding: 10px;
  width: 200px;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 5px;
}

button {
  padding: 10px;
  font-size: 16px;
  cursor: pointer;
}
</style>
