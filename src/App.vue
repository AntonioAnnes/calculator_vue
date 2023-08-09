<script>
import { reactive, computed } from 'vue';


export default {
  setup() {
    const estado = reactive({
      valorA: '',
      valorB: '',
      resultado: '',
      operacao: 'escolha'
    });

    const resultado = computed(() => {
      const { valorA, valorB, operacao } = estado;

      const numA = Number(valorA);
      const numB = Number(valorB);

      switch (operacao) {
        case 'soma':
          return numA + numB;
        case 'multiplicação':
          return numA * numB;
        case 'subtração':
          return numA - numB;
        case 'divisão':
          return numA / numB;
        default:
          return '';
      }
    });

    return {
      estado,
      resultado
    };
  }
}
</script>

<template>
  <div class="container">
    <form>
      <h1>Calculadora</h1>
      <label for ="numeroA">Digite o Valor A</label>
          <input v-model="estado.valorA" type="number" placeholder="Digite o valor aqui...A" class="">
          <label for ="numeroA">Digite o Valor B</label>
          <input v-model="estado.valorB" type="number" placeholder="Digite o valor aqui...B" class="">
            <select v-model="estado.operacao" class="">
              <option value="escolha">Escolha uma operação</option>
              <option value="soma">+</option>
              <option value="multiplicação">*</option>
              <option value="subtração">-</option>
              <option value="divisão">/</option>
            </select>
    </form>
    <h3 v-if="resultado !== ''" class="text-info">Resultado = {{ resultado }}</h3>
  </div>
</template>
<style scoped>
h1 {
  text-align: center;
}
select {
  justify-content: center;
}
</style>