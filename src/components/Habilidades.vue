<template>
  <div class="container">
    <div class="holder">
      <ul>
        <li v-for="(key, value) in habilidades" :key="value">{{ key.nome }}</li>
      </ul>
      <p>These are the skills that you possess.</p>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Habilidades',
    data() {
      return {
        habilidades: [
          { nome: 'PHP'},
          { nome: 'Laravel'},
          { nome: 'JavaScript'},
          { nome: 'Vue.js'}
        ]
      }
    },
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .holder {
    background: #fff;
  }

  ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
  }
  
  ul li {
    padding: 20px;
    font-size: 1.3em;
    background-color: #E0EDF4;
    border-left: 5px solid #3EB3F6;
    margin-bottom: 2px;
    color: #3E5252;
  }

  p {
    text-align:center;
    padding: 30px 0;
    color: gray;
  }

  .container {
    box-shadow: 0px 0px 40px lightgray;
  }
</style>
