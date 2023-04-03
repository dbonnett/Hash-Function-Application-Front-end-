<!-- eslint-disable vue/comment-directive -->
<template>
  <div>
    <p>Hello</p>
    <p>Size of Table: </p>
    <input type="number" v-model="sizeOfTable"/>
    <p>Coefficient: </p>
    <input type="number" v-model="coefficient"/>
    <p>Seed: </p>
    <input type="number" max="sizeOfTable" v-model="seed"/>

    <p>Formula: hash = ({{ coefficient }} * hash * charAt(i)) % {{ sizeOfTable }}</p>
    <p>Enter a word</p>
    <input type="text" v-model="word">
    <p>Hash Value: {{ hash }}</p>
    <div class="table">
      <div v-for="num in table" :key="num" class="element">h</div>
    </div>
  </div>
</template>

<script>
export default {
    name: 'FormulaInput',
    data() {
      return {
        sizeOfTable: 100,
        coefficient: 13,
        seed: 7,
        word: ""
      }
    },
    computed: {
      hash() {
        let h = this.seed;
        for (let i = 0; i < this.word.length; i++) {
          h = (h * this.coefficient * this.word.charCodeAt(i)) % this.sizeOfTable + 1;
        }
        return h;
      },
      table() {
        return Array(this.sizeOfTable);
      }
    }
}
</script>

<style>
    p {
        size: 16;
    }

    .selected {
      color: red;
    }
    
    .table {
      width: 100%;
      display: flex;
      flex-direction: row;
      border: 1px;
      justify-content: space-around;
    }
    
    .table:nth-child(hash()) {
      color: red;
    }
</style>