<template>
  <div class="canvas-wrapper">
    <div :id="canvasId" :style="canvasStyle"></div>
  </div>
</template>

<script>
import p5 from 'p5';

export default {
  name: "VueCanvas",
  props: {
    width: {
      type: Number,
      default: 500
    },
    height: {
      type: Number,
      default: 500
    },
    ballColor: {
      type: Array,
      default: () => [66, 184, 131]
    },
    strokeColor: {
      type: Array,
      default: () => [53, 73, 94]
    },
    canvasId: {
      type: String,
      default: "vue-canvas"
    }
  },
  data() {
    return {
      p5Instance: null,
      speed: 2,
      posX: 35
    };
  },
  computed: {
    canvasStyle() {
      return {
        width: `${this.width}px`,
        height: `${this.height}px`
      };
    }
  },
  mounted() {
    this.createCanvas();
  },
  beforeDestroy() {
    // Clean up p5 instance
    if (this.p5Instance) {
      this.p5Instance.remove();
      this.p5Instance = null;
    }
  },
  methods: {
    createCanvas() {
      const vm = this;
      const script = function(p5) {
        // SETUP::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
        p5.setup = () => {
          const canvas = p5.createCanvas(vm.width, vm.height);
          canvas.parent(vm.canvasId);
        };

        // DRAW:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
        p5.draw = () => {
          p5.background(245);
          const degree = p5.frameCount * 3;
          const y = p5.sin(p5.radians(degree)) * 50;

          p5.push();
          p5.translate(0, p5.height / 2);
          p5.fill(...vm.ballColor);
          p5.stroke(...vm.strokeColor);
          p5.strokeWeight(5);
          p5.ellipse(vm.posX, y, 50, 50);
          p5.pop();
          
          vm.posX += vm.speed;

          if (vm.posX > p5.width - 35 || vm.posX < 35) {
            vm.speed *= -1;
          }
        };
      };
      
      // Create p5 instance
      this.p5Instance = new p5(script);
    }
  }
};
</script>

<style scoped>
  #vue-canvas {
    display: block;
    margin: 0 auto;
    padding: 0;
    border-radius: 20px;
    overflow: hidden;
    
  }
  .canvas-wrapper {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    width: 100%;
  }
</style>