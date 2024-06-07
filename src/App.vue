<template>
  <div id="app" class="container mt-5">
    <Cabecalho />
    <Calculadora />
  </div>
</template>

<script>
import Cabecalho from './components/Cabecalho.vue';
import Calculadora from './components/Calculadora.vue';

export default {
  name: 'App',
  components: {
    Cabecalho,
    Calculadora
  }
};
</script>

<style>

</style>
