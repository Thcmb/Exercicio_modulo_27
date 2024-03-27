<script setup>
  import { reactive } from 'vue';

  const estado = reactive ({
    filtro: '',
    n1: 0,
    n2: 0,
    resultado: 0,
  });

  const soma = (n1, n2) => n1 + n2;
  const subtracao = (n1, n2) => n1 - n2;
  const multiplicacao = (n1, n2) => n1 * n2;
  const divisao = (n1, n2) => (n1 !== 0 && n2 !== 0) ? (n1 / n2) : 'Erro divisão por zero';

  const operacoes = () => {
    const { filtro, n1, n2 } = estado;
  switch (filtro) {
    case "soma":
      estado.resultado = soma(n1, n2);
    break;
    case "subtracao":
      estado.resultado = subtracao(n1, n2);
    break;
    case "multiplicacao":
      estado.resultado = multiplicacao(n1, n2);
    break;
    case "divisao":
      estado.resultado = divisao(n1, n2);
    break;
    default:
      estado.resultado = 0;
    }
  }
</script>

<template>
  <div class="container">
    <div class="content">
      <h1>Calculadora aritmética</h1>
      <label>Primeiro numero</label>
      <input type="number" v-model="estado.n1">
      <label>Segundo numero</label>
      <input type="number" v-model="estado.n2">
      <label>Declare a operaçao: </label>
      <select v-model="estado.filtro" @change="operacoes" class="arit">
        <option value="soma">Somar</option>
        <option value="subtracao">Subtrair</option>
        <option value="multiplicacao">Multiplicar</option>
        <option value="divisao">Dividir</option>
      </select>
      <h3>Resultado: {{ estado.resultado }}</h3>
    </div>
  </div>
  
</template>

<style scoped>
.container {
  max-width: 320px;
  margin: 0 auto;
}

.content {
  background-color: rgb(3, 173, 229);
  padding:10px 30px 10px 30px ;
  border-radius: 8px;
  text-align: center;
}

.arit {
  margin-bottom: 10px;
  height: 30px;
  widows: 30px;
  border-radius: 8px;
  border: none;
}

input {
  display: block;
  margin-bottom: 6px; 
  height: 20px;
  width: 100%;
  text-align: center;
  border-radius: 8px;
  border: none;
}
</style>
