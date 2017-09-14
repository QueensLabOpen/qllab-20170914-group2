<template>
  <div id="app">
    <game></game>
  </div>
</template>

<script>
  import { utils } from 'pixi.js'
  import game from './components/Game.vue'

  export default {
    name: 'app',
    mounted () {
      utils.sayHello()
    },
    components: {
      game
    }
  }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  background: url('./assets/bakgrund_hela.svg') bottom left no-repeat;
  background-size: 80%;
}

  * {
    margin: 0;
    padding: 0;
  }
</style>
