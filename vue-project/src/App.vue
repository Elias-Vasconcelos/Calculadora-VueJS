<script setup>
  import { reactive } from "vue";

  const estado = reactive({
    ValorA: 0,
    ValorB: 0,
    VAlorResultado: 0,
    operacao: "soma"
  })

  const AlteraOperacao = () => {
    const { operacao } = estado
    const { ValorA } = estado
    const { ValorB } = estado

    switch (operacao) {
      case "subtrair":
        return estado.VAlorResultado = ValorA - ValorB;
      case "multiplicar":
        return estado.VAlorResultado = ValorA * ValorB;
      case "Dividir":
        return estado.VAlorResultado = ValorA / ValorB;
      default:
        return estado.VAlorResultado = ValorA + ValorB;
    }
  }





</script>

<template>
  <div class="container mt-5 ">
    <div class="row">
      <form  @keyup="AlteraOperacao()" class="form-control">
        <select @change="evento => estado.operacao = evento.target.value" class="col ms-5 mb-2 btn btn-primary ">
        <option value="somar">somar</option>
        <option value="subtrair">subtrair</option>
        <option value="multiplicar">multiplicar</option>
        <option value="Dividir">Dividir</option>
      </select>
      <ul class="list-grup row">
        <input class="form-control col" type="number" :value="estado.ValorA" @keyup="evento => estado.ValorA =  parseInt(evento.target.value)" place-holder="escolha o Primeiro valor">
        <input class="form-control col" type="number" :value="estado.ValorB" @keyup="evento => estado.ValorB =  parseInt(evento.target.value)" place-holder="escolha o Segundo valor">
      </ul>
        <span class="col btn btn-success" >O resutado é {{ estado.VAlorResultado }}</span>
      </form>
    </div>
  </div>
</template>

<style scoped></style>
