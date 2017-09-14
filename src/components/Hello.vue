<template>
  <div class="hello">

  </div>
</template>

<script>
  import * as PIXI from 'pixi.js'
  export default {
    data () {
      return {
        renderer: null,
        stage: null,
        logo: null,
        x: 0
      }
    },
    name: 'hello',
    mounted () {
      this.renderer = PIXI.autoDetectRenderer(512, 512, {
        resolution: 1,
        transparent: 1
      })

      this.$el.appendChild(this.renderer.view)
      this.stage = new PIXI.Container()

      PIXI.loader.add('logo', require('../assets/logo.png')).load(this.setup)

      window.addEventListener('keypress', () => {
        this.x += 10
      })
    },
    methods: {
      setup () {
        this.logo = new PIXI.Sprite(
          PIXI.loader.resources['logo'].texture
        )

        this.stage.addChild(this.logo)
        this.animationLoop()
      },
      animationLoop () {
        requestAnimationFrame(this.animationLoop)
        this.logo.x = this.x
        this.renderer.render(this.stage)
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
  body {
    background: #9c9c9c;
  }

  canvas {
    border: 2px dotted #9c0c02;
  }
</style>
