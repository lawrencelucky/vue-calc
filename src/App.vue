<template>
  <div id="app">
    <div id="nav">
      <app-calculator></app-calculator>
    </div>
  </div>
</template>

<script>
import Calculator from './views/Calculator';

export default {
  data() {
    return {};
  },
  components: {
    appCalculator: Calculator
  }
};
</script>

<style lang="scss">
html {
  font-size: 62.5%;
  box-sizing: border-box;
}

*,
*::after,
*::before {
  margin: 0;
  padding: 0;
  box-sizing: inherit;
}

body {
  font-size: 1.6rem;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 0;
  padding: 0;
}
</style>
