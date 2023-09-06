<script setup>
import { reactive } from 'vue';

const estado = reactive({
  operacao: '+',
  operador_1: 0,
  operador_2: 0,
  resultado: 0
})

const muda_operador_1 = (e) => {
  estado.operador_1 = e.target.value
  estado.resultado = calcula()
}

const muda_operador_2 = (e) => {
  estado.operador_2 = e.target.value
  estado.resultado = calcula()
}

const muda_operacao = (e) => {
  estado.operacao = e.target.value
  estado.resultado = calcula()
}

const calcula = () => {
  if (estado.operacao == '/' & estado.operador_2 == 0) {
    return 'Operação inválida'
  } else {
    return eval(estado.operador_1 + estado.operacao + estado.operador_2)
  }
}
</script>

<template>
  <div class="container">
    <input @change="muda_operador_1" @keyup="muda_operador_1" type="number" min="0" max="1000000" maxlength="10" size="10" placeholder="">
    <select @change="muda_operacao">
      <option value="+">+</option>
      <option value="-">-</option>
      <option value="*">x</option>
      <option value="/">÷</option>
    </select>
    <input @change="muda_operador_2" @keyup="muda_operador_2" type="number" min="0" max="1000000" maxlength="10" size="10" placeholder="">
    <span class="equal">=</span> <span class="resultado">{{ estado.resultado }}</span>
  </div>
</template>

<style scoped>
.container {
  font-family: sans-serif;
  max-width: 960px;
  width: 100%;
  margin: 80px auto;
  text-align: center;
}

input, select {
  margin-left: 8px;
  font-family: sans-serif;
  padding: 1rem 1rem;
  font-size: 2rem;
  border: 1px solid #4A4A48;
  border-radius: 3px;
  background: #fff;
  color: #4A4A48;
}

select {
  cursor: pointer;
}

option {
  color: #4A4A48;
}
.equal, .resultado {
  font-size: 2rem;
  color: #4A4A48;
  margin-left: 8px;
}
</style>
