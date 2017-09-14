<template>
<div class="wrapper">
  <div>
    var player = function Player(name){
      <div>this.name = {{player.name}};</div>
      <div>
        this.backpack = [</br>
        <div v-for="(item,index) in player.backpack" :key="item">
          {{item}}
          <span v-if="index != player.backpack.length - 1">,</span>
        </div>
        ];
      </div>
      <div :class="{'is-active': moveActive}">this.move = function(x, y){
        }</div>
       <div>this.collectMatches = function (){}</div>
       <div>this.startFire = function(){}</div>
    };<br />
  </div>

  <div class="consoler"></div>
</div>

</template>

<script>
export default {
  props: {
    moveActive: Boolean
  },
  name: 'codeDisplayer',
  data () {
    return {
      world: {
        name: 'woods',
        items: ['firewood'],
        fireplace: {
          isOnFire: false
        }
      },
      player: {
        name: 'satan',
        backpack: ['matchbox', 'firewood']
      }
    }
  }

}
</script>

<style>
  .wrapper {
    width: calc(20% - 44px);
    display: inline-block;
    font-size: 0.7em;
    vertical-align: top;
    height: calc(100% - 18px);
    border: 1px solid #000;
  }

  div {
    padding: 10px;
  }

  .is-active {
    background: yellow;
  }

</style>


