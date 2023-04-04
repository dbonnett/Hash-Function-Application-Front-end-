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
    <div class="space"></div>
    <div class="table">
      <div v-for="num in table" :key="num" class="bar"></div>
    </div>
    <div class="table">
      <div v-for="num in table" :key="num" class="element">{{ num }}</div>
    </div>
  </div>
</template>

<script>
export default {
    name: 'FormulaInput',
    data() {
      return {
        sizeOfTable: 60,
        coefficient: 13,
        seed: 7,
        word: "",
        test: "15px"
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
        let tab = Array(this.sizeOfTable);
        for(let i = 0; i < this.sizeOfTable; i++) {
          tab[i] = i + 1;
        }
        return tab;
      }
    }
}
</script>

<style>

    .selected {
      color: red;
    }
    
    .element {
      font-size: 16px;
    }
    
    .table {
      width: 90%;
      margin: auto;
      display: flex;
      flex-direction: row;
      border: 1px;
      justify-content: space-around;
    }
    
    .element:nth-child() {
      color: red;
      font-size: 20px;
    }
    
    .space {
      height: 100px;
    }
    
    .bar {
      height: var(--test);
      width: 10px;
      padding: none;
      margin: 1px;
      background-color: green;
    }
</style>