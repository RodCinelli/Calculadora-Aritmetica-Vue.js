<template>
    <div>
        <input type="number" class="form-control form-control-sm custom-input" :value="valor" @input="atualizarValor" />
    </div>
</template>

<script>
export default {
    name: 'NumeroInput',
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
        atualizarValor(event) {
            this.$emit('input', parseFloat(event.target.value));
        }
    }
};
</script>

<style scoped>
.custom-input {
    color: #495057;
    background-color: #f8f9fa;
}
</style>