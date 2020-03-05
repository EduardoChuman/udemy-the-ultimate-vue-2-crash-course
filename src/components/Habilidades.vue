<template>
  <div class="container">
    <form @submit.prevent="incluirHabilidade">
      <input type="text" placeholder="Informe sua habilidade aqui..." v-model="habilidade" v-validate="'min:3'" name="habilidade">
      <transition name="alert-in" enter-active-class="animated zoomInDown" leave-active-class="animated fadeOutUp">
        <p class="alert" v-if="errors.has('habilidade')">{{ errors.first('habilidade') }}</p>
      </transition>
    </form>
    {{ habilidade }}
    <div class="holder">
      <ul>
        <transition-group name="list" enter-active-class="animated bounceInUp" leave-active-class="animated bounceOutDown">
          <li v-for="(key, value) in habilidades" :key="value">{{ key.nome }}</li>
        </transition-group>
      </ul>
      <p>Essas são as habilidades que você registrou.</p>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Habilidades',
    data() {
      return {
        habilidade: '',
        habilidades: [
          { nome: 'Excel'},
          // { nome: 'Laravel'},
          // { nome: 'JavaScript'},
          // { nome: 'Vue.js'}
        ]
      }
    },
    methods: {
      incluirHabilidade() {
        this.$validator.validateAll().then((result) => {
          if (result) {
            this.habilidades.push({nome:  this.habilidade});
            this.habilidade = '';
          } else {
            console.log('Not valid');
          }
        })
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  @import "https://cdn.jsdelivr.net/npm/animate.css@3.5.1";
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

  input {
    width: calc(100% - 40px);
    border: 0;
    padding: 20px;
    font-size: 1.3em;
    background-color: #323333;
    color: #687F7F;
  }

  .alert {
    background: #fdf2ce;
    font-weight: bold;
    display: inline-block;
    padding: 5px;
    margin-top: -20px;
  }

  .alert-in-enter-active {
    animation: bounce-in .5s;
  }
  .alert-in-leave-active {
    animation: bounce-in .5s reverse;
  }
  @keyframes bounce-in {
    0% {
      transform: scale(0);
    }
    50% {
      transform: scale(1.5);
    }
    100% {
      transform: scale(1);
    }
  }
</style>
