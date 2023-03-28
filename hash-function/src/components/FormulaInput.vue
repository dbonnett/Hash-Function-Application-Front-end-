<!-- eslint-disable vue/comment-directive -->
<template>
  <div>
    <p>Hello</p>
    <p>Size of Table: </p>
    <input type="number" v-model="sizeOfTable"/>
    <p>Coefficient: </p>
    <input type="number" v-model="coefficient"/>
    <p>Seed: </p>
    <input type="number" v-model="seed"/>

    <p>Formula: hash = ({{ coefficient }} * hash * charAt(i)) % {{ sizeOfTable }}</p>
    <p>Enter a word</p>
    <input type="text" v-model="word">
    <p>Hash Value: {{ hash }}</p>
  </div>
</template>

<script>
export default {
    name: 'FormulaInput',
    data() {
      return {
        sizeOfTable: 100,
        coefficient: 13,
        seed: 0,
        word: ""
      }
    },
    computed: {
      hash() {
        let h = 0;
        for (let i = 0; i < this.word.length; i++) {
          h = (h * this.coefficient * this.word.charAt(i)) % this.sizeOfTable;
        }
        return h;
      }
    }
}
</script>

<style>
    p {
        size: 16;
    }
</style>