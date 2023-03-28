<!-- eslint-disable vue/comment-directive -->
<template>
  <div>
    <p>Hello</p>
    <p>Size of Table: </p>
    <input type="number" v-model="sizeOfTable"/>
    <p>Coefficient: </p>
    <input type="number" value="13"/>
    <p>Seed: </p>
    <input type="number" value="0"/>

    <p>Formula: </p>
    <p>Enter a word</p>
    <input type="text">
  </div>
</template>

<script>
export default {
    name: 'FormulaInput',
    data() {
      return {
        sizeOfTable: 50,
        coefficient: 13
      }
    }
}
</script>

<style>
    p {
        size: 16;
    }
</style>