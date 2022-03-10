<template>
  <div id="app">
    <div class="top">
     <h1>Calculator with</h1>
     <img alt="Vue logo" src="./assets/logo.png" height="80px"> 
    </div>
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
.top {
  font-weight: bold;
  color: #f7f7f7;
  display: flex;
  justify-content: center;

  h1 {
   font-size: 40px;
  }
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
body{
  background-color: #35495e;
}

</style>
