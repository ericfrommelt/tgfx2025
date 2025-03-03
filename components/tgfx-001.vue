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
            default: 1080
            },
            height: {
            type: Number,
            default: 1080
            },
            ballColor: {
            type: Array,
            default: () => [0, 0, 0]
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
            speed: 4,
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
            let script = function(p5) {
                let font;
                let fontMono;
                let c = p5.color(255, 255, 255);
                let background = p5.color(30, 30, 30);
                let brandGreen = p5.color(229, 252, 96);
                let bgblack = p5.color(0, 0, 0);
                let neonGreen = p5.color(96, 252, 96);
                let yellow = p5.color(229, 252, 96);
                let orange = p5.color(252, 221, 96);
                let babyBlue = p5.color(129, 242, 255);
                let eveningBlue = p5.color(112, 164, 219);
                let purple = p5.color(217, 151, 246);
                let pink = p5.color(255, 47, 148);
                
                let colors = [brandGreen, neonGreen, yellow, orange, babyBlue, eveningBlue, purple];
                
                let tgfx = ["T", "E", "K", "N", "O", "G", "R", "A", "F", "I", "X"];
                let xy = [100, 200, 300, 400, 500, 600, 700, 800, 900];
                
                // Text vector positions
                let p1 = p5.createVector(xy[p5.floor(p5.random(9))], xy[p5.floor(p5.random(9))]);
                let p2 = p5.createVector(xy[p5.floor(p5.random(9))], xy[p5.floor(p5.random(9))]);
                let p3 = p5.createVector(xy[p5.floor(p5.random(9))], xy[p5.floor(p5.random(9))]);
                let p4 = p5.createVector(xy[p5.floor(p5.random(9))], xy[p5.floor(p5.random(9))]);
                let p5a = p5.createVector(xy[p5.floor(p5.random(9))], xy[p5.floor(p5.random(9))]);
                let p6 = p5.createVector(xy[p5.floor(p5.random(9))], xy[p5.floor(p5.random(9))]);
                let p7 = p5.createVector(xy[p5.floor(p5.random(9))], xy[p5.floor(p5.random(9))]);
                let p8 = p5.createVector(xy[p5.floor(p5.random(9))], xy[p5.floor(p5.random(9))]);
                let p9 = p5.createVector(xy[p5.floor(p5.random(9))], xy[p5.floor(p5.random(9))]);
                let p10 = p5.createVector(xy[p5.floor(p5.random(9))], xy[p5.floor(p5.random(9))]);
                let p11 = p5.createVector(xy[p5.floor(p5.random(9))], xy[p5.floor(p5.random(9))]);
                
                // A vector positions
                let a1 = p5.createVector(300, 900);
                let a2 = p5.createVector(540, 200);
                let a3 = p5.createVector(656, 540);
                let a4 = p5.createVector(694, 640);
                let a5 = p5.createVector(780, 900);
                let a6 = p5.createVector(540, 640);
                
               

                p5.preload = function() {
                    font = p5.loadFont('/IBMPlexSans-Bold.ttf');
                    fontMono = p5.loadFont('/IBMPlexMono-Regular.ttf');
                    console.log("fonts loaded");
                };

                // SETUP::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
                p5.setup = () => {
                const canvas = p5.createCanvas(vm.width, vm.height);
                canvas.parent(vm.canvasId);
                mover = createMover();
                moverTwo = createMover();
                moverThree = createMover();

                console.log("setup initialized");
                };

                // DRAW:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
                p5.draw = () => {
                    p5.background(background);
                    const degree = p5.frameCount * 3;
                    const y = p5.sin(p5.radians(degree)) * 50;

                    p5.push();
                    p5.translate(0, p5.height / 2);
                    p5.noStroke();
                    p5.fill(neonGreen);
                    // p5.stroke(vm.strokeColor);
                    // p5.strokeWeight(5);
                    p5.ellipse(vm.posX, y, 20, 20);
                    p5.pop();
                    
                    vm.posX += vm.speed;

                    if (vm.posX > p5.width - 10 || vm.posX < 10) {
                        vm.speed *= -1;
                        // drawTxt();
                    }

                    drawTxt();
                    drawGrid(10, 10);
                    mover.update();
                    mover.show();
                    mover.checkEdges();
                    moverTwo.update();
                    moverTwo.show();
                    moverTwo.checkEdges();
                    moverThree.update();
                    moverThree.show();
                    moverThree.checkEdges();
                    capitalA().show();
                    techShit(140, 100, 3, 3);
                    techShit(140, 200, 3, 3);
                    techShit(140, 300, 3, 3);
                    techShit(940, 300, 30, 10);
                    techShit(640, 960, 10, 6);
                    drawTxtTwo(600, 900);
                    circleGrid(100, 100, 4, 4);
                 
            };

            let techShit = (x, ty, w, pad) => {
                p5.stroke(bgblack);
                p5.strokeWeight(2);
                for (let i = 0; i < 10; i++) {
                    p5.line(x, ty, x + w, ty);
                    ty += pad;
                }
            }

            let bigCrosshair = () => {
                p5.strokeWeight(2);
                p5.stroke(neonGreen);
                p5.line(p5.width / 2, 100, p5.width / 2, p5.height - 100);
                p5.line(100, p5.height / 2, p5.width - 100, p5.height / 2);
            }

            let circleGrid = (x, y, d, num) => {
                p5.fill(bgblack);
                p5.noStroke();
                for (let i = 0; i < num; i++) {
                    x += 4;
                    for (let j = 0; j < num; j++) {
                        p5.circle(x, y, d);
                        y += 4;
                    }
                }
            }

            let drawTxt = () => {
                p5.noStroke();
                p5.fill(yellow);
                p5.textFont(font);
                p5.textSize(14);
                p5.text(tgfx[0], p1.x, p1.y);
                p5.text(tgfx[1], p2.x, p2.y);
                p5.text(tgfx[2], p3.x, p3.y);
                p5.text(tgfx[3], p4.x, p4.y);
                p5.text(tgfx[4], p5a.x, p5a.y);
                p5.text(tgfx[5], p6.x, p6.y);
                p5.text(tgfx[6], p7.x, p7.y);
                p5.text(tgfx[7], p8.x, p8.y);
                p5.text(tgfx[8], p9.x, p9.y);
                p5.text(tgfx[9], p10.x, p10.y);
                p5.text(tgfx[10], p11.x, p11.y);
            }

            let drawTxtTwo = () => {
                p5.noStroke();
                p5.fill(purple);
                p5.textFont(fontMono);
                p5.textSize(10);
                p5.rotate(0);
                p5.text("TGFX :: Brand Grafix", 900, 800);
            }

            let drawGrid = (cols, rows) => {
                p5.stroke(0);
                p5.strokeWeight(1);
                for (let i = 1; i < cols; i++) {
                    for (let j = 1; j < rows; j++) {
                        p5.line(
                            i * p5.width / cols, 
                            p5.width / cols, 
                            i * p5.width / cols, 
                            p5.height - p5.width / cols
                        );
                        p5.line(
                            p5.height / rows, 
                            j * p5.height / rows, 
                            p5.width - p5.height / rows, 
                            j * p5.height / rows
                        );
                    }
                }
            }

            let mover, moverTwo, moverThree;
            
            let createMover = () => {
                return {
                    position: p5.createVector(p5.random(p5.width), p5.random(p5.height)),
                    velocity: p5.createVector(p5.random(-2, 2), p5.random(-2, 2)),
                    update: function() {
                        this.position.add(this.velocity);
                    },
                    show: function() {
                        p5.noStroke();
                        p5.fill(p5.random(colors));
                        p5.ellipse(this.position.x, this.position.y, 20, 20);
                    },
                    checkEdges: function() {
                        if (this.position.x > p5.width) {
                            this.position.x = 0;
                        } else if (this.position.x < 0) {
                            this.position.x = p5.width;
                        }

                        if (this.position.y > p5.height) {
                            this.position.y = 0;
                        } else if (this.position.y < 0) {
                            this.position.y = p5.height;
                    }
                    }
                };
            }

            let capitalA = () => {
                return {
                    show: function(){
                        let gradient = p5.drawingContext.createLinearGradient(300, 900, 700, 200);
                        p5.noFill();
                        p5.strokeWeight(100);
                        p5.strokeJoin(p5.ROUND);
                        p5.strokeCap(p5.ROUND);
                        
                        gradient.addColorStop(0, yellow);
                        gradient.addColorStop(0.5, orange);
                        gradient.addColorStop(1, babyBlue);

                        p5.drawingContext.strokeStyle = gradient;
                        p5.drawingContext.beginPath();
                        p5.drawingContext.moveTo(a1.x, a1.y);
                        p5.drawingContext.lineTo(a2.x, a2.y);
                        p5.drawingContext.lineTo(a3.x, a3.y);
                        p5.drawingContext.stroke();
                        p5.drawingContext.closePath();

                        p5.strokeWeight(60);
                        p5.drawingContext.strokeStyle = pink;
                        p5.drawingContext.beginPath();
                        p5.drawingContext.moveTo(a4.x, a4.y);
                        p5.drawingContext.lineTo(a5.x, a5.y);
                        p5.drawingContext.stroke();
                        p5.drawingContext.closePath();

                        p5.fill(babyBlue);
                        p5.circle(a6.x, a6.y, 100); 
                    }
                }
            }

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