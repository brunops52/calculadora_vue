<script setup>
import { reactive } from 'vue';
const estado = reactive({
  campo1: 0,
  campo2: 0,
  operacao: "somar",
  resultado: 0,
})
const soma = () => {
return parseFloat(estado.campo1) + parseFloat(estado.campo2)
}
const subtracao = () => {
return parseFloat(estado.campo1) - parseFloat(estado.campo2)
}
const divisao = () => {
return parseFloat(estado.campo1) / parseFloat(estado.campo2)
}
const multiplicacao = () => {
return parseFloat(estado.campo1) * parseFloat(estado.campo2)
}
const escolheOperacao = () => {
    const {operacao} = estado;

    switch (operacao) {
        case "soma" :
            return soma();
        case "subtracao" :
            return subtracao();
        case "divisao" :
            return divisao();
        case "multiplicacao" :
            return multiplicacao();
    }
}

</script>

<template>
  <div class="container pb-md-5">
    <header class="p-5 mb-4 mt-4 text-center">
      <h1>Calculadora</h1>
    </header>
    <form>
      <div class="row">
        <div class="col-md-4">
          <input @keyup="evento => estado.campo1 = evento.target.value" type="number" class="form-control">
        </div>
        <div class="col-md-4">
          <input @keyup="evento => estado.campo2 = evento.target.value" type="number" class="form-control">
        </div>
        <div class="col-md-4">
          <select @change="evento => estado.operacao = evento.target.value">
            <option>Escolha</option>
            <option value="soma">Somar</option>
            <option value="subtracao">Subtrair</option>
            <option value="divisao">Dividir</option>
            <option value="multiplicacao">Multiplicar</option>
          </select>
        </div>
      </div>
    </form>
    <div class="resultado mt-5 text-center">
      <h2>A {{estado.operacao}} resultou em {{ escolheOperacao() }}.</h2>
    </div>
  </div>
</template>

<style scoped>
.container{
  width: 600px;
  background-color: rgb(120, 151, 151);
}
h1,h2{
  font-weight: 900;
  color: rgb(1, 27, 49);
}
</style>
