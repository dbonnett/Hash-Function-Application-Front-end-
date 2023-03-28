<template>
  <FormulaInput></FormulaInput>
</template>

<script>
import FormulaInput from './components/FormulaInput.vue'

export default {
  name: 'App',
  components: {
    FormulaInput
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
