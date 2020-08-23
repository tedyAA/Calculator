<template>
  <div id="app">
    <nav class="navbar navbar-light bg-light">
      <a class="navbar-brand">
        <img src="./assets/logo.png" width="30" height="30" class="d-inline-block align-top" alt="">
        Calculator
      </a>
    </nav>
    <calculator/>
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

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}

</style>
