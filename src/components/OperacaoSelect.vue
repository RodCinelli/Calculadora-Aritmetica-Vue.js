<template>
    <div>
        <select class="form-control form-control-sm custom-select" :value="valor" @change="atualizarOperacao">
            <option value="soma">+</option>
            <option value="subtracao">-</option>
            <option value="multiplicacao">*</option>
            <option value="divisao">/</option>
        </select>
    </div>
</template>

<script>
export default {
    name: 'OperacaoSelect',
    props: ['value'],
    data() {
        return {
            valor: this.value
        };
    },
    watch: {
        value(newValue) {
            this.valor = newValue;
        }
    },
    methods: {
        atualizarOperacao(event) {
            this.$emit('input', event.target.value);
        }
    }
};
</script>

<style scoped>
.custom-select {
    color: #495057;
    background-color: #f8f9fa;
}
</style>