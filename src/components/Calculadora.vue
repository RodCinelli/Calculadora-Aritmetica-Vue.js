<template>
    <div class="card p-4">
        <div class="form-group mb-4">
            <input type="number" class="form-control form-control-sm custom-input" v-model="estado.primeiroNumero"
                @input="calcularResultado" />
        </div>
        <div class="form-group mb-4">
            <select class="form-control form-control-sm custom-select" v-model="estado.operacaoMatematica"
                @change="calcularResultado">
                <option value="soma">+</option>
                <option value="subtracao">-</option>
                <option value="multiplicacao">*</option>
                <option value="divisao">/</option>
            </select>
        </div>
        <div class="form-group mb-4">
            <input type="number" class="form-control form-control-sm custom-input" v-model="estado.segundoNumero"
                @input="calcularResultado" />
        </div>
        <p>Resultado: {{ estado.resultado }}</p>
    </div>
</template>

<script setup>
import { reactive, watch } from 'vue';

const estado = reactive({
    primeiroNumero: 0,
    segundoNumero: 0,
    operacaoMatematica: 'soma',
    resultado: 0,
    operacoes: {
        soma: (a, b) => a + b,
        subtracao: (a, b) => a - b,
        multiplicacao: (a, b) => a * b,
        divisao: (a, b) => (b !== 0 ? a / b : 'Divisão por zero')
    }
});

const calcularResultado = () => {
    const { primeiroNumero, segundoNumero, operacaoMatematica } = estado;
    estado.resultado = estado.operacoes[operacaoMatematica](parseFloat(primeiroNumero), parseFloat(segundoNumero));
};

// Reatividade para calcular automaticamente ao alterar qualquer valor
watch(
    () => [estado.primeiroNumero, estado.segundoNumero, estado.operacaoMatematica],
    calcularResultado
);

// Calcular resultado inicial
calcularResultado();
</script>

<style scoped>
/* Estilos da calculadora */
.card {
    max-width: 400px;
    margin: 0 auto;
}

.custom-input {
    color: #495057;
    background-color: #f8f9fa;
}

.custom-select {
    color: #495057;
    background-color: #f8f9fa;
}
</style>