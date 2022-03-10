<template>
  <div id="app">
   
    <h1>Calculator</h1>
    <!--  <img alt="Vue logo" src="./assets/logo.png"> -->
    <Calculator/>
  </div>
</template>

<script>
import Calculator from './components/Calculator.vue'
export default {
  name: 'App',
  components: {
    Calculator
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
body{
  background-color:#2c3e50;
}
</style>
