<script setup>
import { ref, computed } from 'vue';

// Variáveis reativas
const numero1 = ref(0);
const numero2 = ref(0);
const operacao = ref('soma');

// Computed para calcular o resultado
const resultado = computed(() => {
  const num1 = parseFloat(numero1.value);
  const num2 = parseFloat(numero2.value);

  switch (operacao.value) {
    case 'soma':
      return num1 + num2;
    case 'subtracao':
      return num1 - num2;
    case 'multiplicacao':
      return num1 * num2;
    case 'divisao':
      return num2 !== 0 ? num1 / num2 : 'Erro: Divisão por zero';
    default:
      return 0;
  }
});
</script>

<template>
  <div class="container mt-5">
    <div class="row justify-content-center">
      <div class="col-md-6">
        <div class="card">
          <div class="card-header bg-primary text-white">
            <h3 class="card-title text-center">Calculadora Aritmética</h3>
          </div>
          <div class="card-body">
            <!-- Campo para o primeiro número -->
            <div class="mb-3">
              <label for="numero1" class="form-label">Número 1:</label>
              <input id="numero1" type="number" v-model="numero1" class="form-control"
                placeholder="Digite o primeiro número" />
            </div>

            <!-- Campo para o segundo número -->
            <div class="mb-3">
              <label for="numero2" class="form-label">Número 2:</label>
              <input id="numero2" type="number" v-model="numero2" class="form-control"
                placeholder="Digite o segundo número" />
            </div>

            <!-- Select para escolher a operação -->
            <div class="mb-3">
              <label for="operacao" class="form-label">Operação:</label>
              <select id="operacao" v-model="operacao" class="form-select">
                <option value="soma">Soma</option>
                <option value="subtracao">Subtração</option>
                <option value="multiplicacao">Multiplicação</option>
                <option value="divisao">Divisão</option>
              </select>
            </div>

            <!-- Exibição do resultado -->
            <div class="mt-4">
              <h4 class="text-center">
                Resultado: <span class="badge bg-success">{{ resultado }}</span>
              </h4>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card {
  border: 1px solid #ddd;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.card-header {
  border-radius: 8px 8px 0 0;
}

.badge {
  font-size: 1.25rem;
  padding: 0.5rem 1rem;
}
</style>
