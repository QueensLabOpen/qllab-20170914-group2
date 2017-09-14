<template>
  <div class="hello"></div>
</template>

<script>
  import * as PIXI from 'pixi.js'

  export default {
    data () {
      return {
        renderer: null,
        stage: null,
        whacka: null,
        x: 0,
        y: 400,
        groundLevel: 400,
        keyState: {},
        JumpState: false,
        pSpeedY: 0
      }
    },
    name: 'hello',
    mounted () {
      this.renderer = PIXI.autoDetectRenderer(window.innerWidth * 0.8, 700, {
        resolution: 1,
        transparent: 1
      })

      this.$el.appendChild(this.renderer.view)
      this.stage = new PIXI.Container()

      PIXI.loader.add('whacka', require('../assets/with-backpack.svg')).load(this.setup)
    },
    methods: {
      keyListener () {
        const keyState = {}

        window.addEventListener('keydown', (e) => {
          keyState[e.keyCode || e.which] = true
        }, true)

        window.addEventListener('keyup', (e) => {
          keyState[e.keyCode || e.which] = false
        }, true)

        setInterval(() => {
          if (keyState[37] || keyState[65]) {
            this.x -= 3
          }

          if (keyState[39] || keyState[68]) {
            this.x += 3
          }

          if ((keyState[87] || keyState[38]) && this.y === this.groundLevel) {
            this.pSpeedY = 15
          }
        }, 10)
      },
      setup () {
        this.whacka = new PIXI.Sprite(
          PIXI.loader.resources['whacka'].texture
        )

        this.whacka.scale.set(0.3)
        // this.whacka.pivot

        this.stage.addChild(this.whacka)
        this.animationLoop()
        this.keyListener()
      },
      animationLoop () {
        this.y = this.y - this.pSpeedY

        if (this.y < this.groundLevel) {
          // this.whacka.rotation += window.Math.PI / 15
          this.pSpeedY -= 1
        } else {
          this.pSpeedY = 0
          this.y = this.groundLevel
        }

        requestAnimationFrame(this.animationLoop)
        this.whacka.x = this.x
        this.whacka.y = this.y

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
