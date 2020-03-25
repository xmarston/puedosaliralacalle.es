<style>

  html {
    height: 100%;
  }

  body {
    background: #000000;
    margin: 0;
    padding: 0;
    height: 100%;
  }

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #ffffff;
    font-weight: bold;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    width: 100%;
    text-align: center;
    height: 100%;
  }

</style>

<template>

  <div id="app">
    <Warning/>
  </div>

</template>

<script>

  import Warning from './components/Warning.vue'

  export default {
    name: 'App',
    components: {
      Warning
    }
  }

</script>
