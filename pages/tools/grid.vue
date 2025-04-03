  <script>
    import p5 from "p5";
    export default {
      name: "VueCanvas",
      props: {
        width: {
          type: Number,
          default: 800
        },
        height: {
          type: Number,
          default: 800
        },
        canvasId: {
          type: String,
          default: "vue-canvas"
        }
      },
      data() {
        return {
          p5Instance: null,
          speed: 4,
          posX: 35,
          weight: 1,
          rows: 10,
          cols: 10
        };
      },
      mounted() {
        this.$nextTick(() => {
          this.initializeCanvas();
        });
      },
      beforeUnmount() {
        if (this.p5Instance) {
          this.p5Instance.remove();
          this.p5Instance = null;
        }
      },
      methods: {
        initializeCanvas() {
          const container = this.$refs.canvasContainer;
  
          if (!container) {
            console.error("Canvas container ref not found");
            return;
          }
  
          this.p5Instance = new p5((p) => {
            let background = p.color(30, 30, 30);
            // Save component reference for easier access
            const vm = this;
  
            p.setup = () => {
              console.log("Setting up canvas with dimensions:", vm.width, vm.height);
              p.createCanvas(vm.width, vm.height);
            }
  
            p.draw = () => {
              p.background(background);
              p.fill(255);
              p.ellipse(p.width / 2, p.height / 2, 50, 50);
              drawGrid(10, 10);
            }

            let drawGrid = (cols, rows) => {
              p.stroke(0);
              p.strokeWeight(vm.weight);
              for (let i = 1; i < this.cols; i++) {
                for (let j = 1; j < this.rows; j++) {
                  p.line(
                      i * p.width / this.cols, 
                      p.width / this.cols, 
                      i * p.width / this.cols, 
                      p.height - p.width / this.cols
                  );
                  p.line(
                      p.height / this.rows, 
                      j * p.height / this.rows, 
                      p.width - p.height / this.rows, 
                      j * p.height / this.rows
                  );
                }
              }
            }
          }, container);
        }
      }  
    }
  </script>

<template>
  <div class="canvas-wrapper">
    <div ref="canvasContainer" class="canvas-container"></div>
    <div class="controls">
      <input type="range" v-model.number="speed" min="1" max="10" step="1" />
      <div class="speed-display">Speed: {{ speed }}</div>
      <input type="range" v-model.number="weight" min="1" max="20" step="1" />
      <div class="speed-display">Weight: {{ weight }}</div>
      <input type="range" v-model.number="cols" min="1" max="200" step="1" />
      <div class="speed-display">Columns: {{ cols }}</div>
      <input type="range" v-model.number="rows" min="1" max="200" step="1" />
      <div class="speed-display">Rows: {{ cols }}</div>
    </div>
  </div>
</template>

<style scoped>
  .canvas-container {
    display: block;
    margin: 0 auto;
    padding: 0;
    /* border-radius: 20px; */
    overflow: hidden;
    width: 800px;
    height: 800px;
    background-color: #1e1e1e;
  }
  
  .canvas-wrapper {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    height: 100%;
    width: 100%;
  }

  .controls {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-left: 40px;
  }
  
  input[type="range"] {
    width: 100px;
    margin-top: 20px;
  }
</style>