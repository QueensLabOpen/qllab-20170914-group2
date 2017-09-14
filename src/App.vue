<template>
  <div id="app">
    <game v-on:toggleActive="toggleActive"></game>
    <code-displayer :moveActive="isActive"></code-displayer>
  </div>
</template>

<script>
  import { utils } from 'pixi.js'
  import game from './components/Game.vue'
  import codeDisplayer from './components/CodeDisplayer.vue'

  export default {
    name: 'app',
    data () {
      return {
        isActive: false
      }
    },
    mounted () {
      utils.sayHello()
    },
    methods: {
      toggleActive(value) {
        this.isActive = value
      }
    },
    components: {
      game,
      codeDisplayer
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;d
    -moz-osx-font-smoothing: grayscale;
    text-align: left;
    color: #2c3e50;
    background: url('./assets/bakgrund_hela.svg') bottom left no-repeat;
    background-size: 80%;
    padding: 0;
    height: 700px;
  }

  * {
    margin: 0;
    padding: 0;
  }
</style>
