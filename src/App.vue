<template>
  <div class="container">
    <header class="p-5 mt-4 bg-dark text-light text-center rounded-3">
      <h1>Calculadora aritmetica</h1>
    </header>
    <form class="bg-light pt-4">
      <div class="row">
        <div class="col-2">
          <input @keyup="evento => estado.numero1 = evento.target.value" type="number" v-model.number="num1" placeholder="1° numero" class="form-control text-center">
        </div>
        <div class="col-3">
          <select v-model="operacao" class="form-control bg-secondary text-light text-center m-0">
            <option value="+">(+) Soma</option>
            <option value="-">(-) Subtração</option>
            <option value="*">(x) Multiplicação</option>
            <option value="/">(÷) Divisão</option>
          </select>
        </div>
        <div class="col-2">
          <input @keyup="evento => estado.numero2 = evento.target.value" type="number" v-model.number="num2" placeholder="2° numero" class="form-control text-center">
        </div>
        <div class="col-2 d-inline align-content-center text-end">
          <b>RESULTADO:</b>
        </div>
        <div class="resultado col-3 rounded-2 bg-dark text-light p-0 d-inline align-content-center text-center">
          {{ resultado }}
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      num1: 0,
      num2: 0,
      operacao: '+'
    };
  },
  computed: {
    resultado() {
      switch (this.operacao) {
        case '+':
          return this.num1 + this.num2;
        case '-':
          return this.num1 - this.num2;
        case '*':
          return this.num1 * this.num2;
        case '/':
          return this.num2 !== 0 ? this.num1 / this.num2 : 'Erro: divisão por zero';
        default:
          return 'Operação inválida';
      }
    }
  }
};
</script>

<style scoped>
  .container {
    max-width: 1024px;
  }

  .resultado {
    max-width: 20%;
    margin-left: 2%;
    height: 38px;
    max-height: 100%;
  }
</style>
