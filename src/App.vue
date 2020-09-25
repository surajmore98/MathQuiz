<template>
  <div id="app">
    <h1> Math Quiz App </h1>
    <operator-quiz @on-back="clearOperator" v-if="operator"  :operator="operator"/>
    <operator-selector v-if="!operator" @select-operator="selectOperator"/>
  </div>
</template>

<script>
import OperatorSelector from './components/OperatorSelector.vue'
import OperatorQuiz from './components/OperatorQuiz.vue'


export default {
  name: 'App',
  components: {
    OperatorSelector,
    OperatorQuiz
  },
  data() {
    return {
      operator: null
    }
  },
  methods: {
    selectOperator(operator){
      console.log(operator);
      this.operator = operator;
    },
    clearOperator(){
      this.operator = null;
    }
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

button{
  padding: 10px;
  width: 200px;
  margin-right: 10px;
  height: 80px;
  background-color: #10aeb2;
  color: white;
  font-size: 24px;
}
</style>
