<template>
  <div id="app">
    <Habilidades/>    
  </div>
</template>

<script>
  import Habilidades from './components/Habilidades.vue'

  export default {
    name: 'App',
    components: {
      Habilidades
    },
  }
</script>

<style>
  @import url('https://fonts.googleapis.com/css?family=Montserrat:400,700');

  body {
    background-color: #EEEEEE;
    font-family: 'Montserrat', sans-serif;
    display: grid;
    grid-template-rows: auto;
    justify-items: center;
    align-items: center;
  }
  body, html {
    margin: 0;
    height: 100%;
  }
  #app {
      width: 50%;
  }
</style>
