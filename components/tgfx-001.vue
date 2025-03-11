<template>
    <div class="canvas-wrapper">
        <div ref="canvasContainer" class="canvas-container"></div>
        <div class="controls">
            <input type="range" v-model.number="speed" min="1" max="10" step="1" />
            <div class="speed-display">Speed: {{ speed }}</div>
            <input type="range" v-model.number="weight" min="20" max="300" step="1" />
            <div class="speed-display">Weight: {{ weight }}</div>
        </div>
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
                posX: 35,
                weight: 120,
            };
        },
        mounted() {
            // Use this.$nextTick to ensure DOM is ready
            this.$nextTick(() => {
                this.initializeCanvas();
            });
        },
        beforeUnmount() {
            // Clean up p5 instance
            if (this.p5Instance) {
                this.p5Instance.remove();
                this.p5Instance = null;
            }
        },
        methods: {
            initializeCanvas() {
                const container = this.$refs.canvasContainer;
                
                if (!container) {
                    console.error('Canvas container ref not found');
                    return;
                }
                
                // Create a new p5 instance with the sketch function
                this.p5Instance = new p5((p) => {
                    let font;
                    let fontMono;
                    let background = p.color(30, 30, 30);
                    let brandGreen = p.color(229, 252, 96);
                    let bgblack = p.color(0, 0, 0);
                    let neonGreen = p.color(96, 252, 96);
                    let yellow = p.color(229, 252, 96);
                    let orange = p.color(252, 221, 96);
                    let babyBlue = p.color(129, 242, 255);
                    let eveningBlue = p.color(112, 164, 219);
                    let purple = p.color(217, 151, 246);
                    let pink = p.color(255, 47, 148);
                    
                    let colors = [brandGreen, neonGreen, yellow, orange, babyBlue, eveningBlue, purple];
                    
                    let tgfx = ["T", "E", "K", "N", "O", "G", "R", "A", "F", "I", "X"];
                    let xy = [100, 200, 300, 400, 500, 600, 700, 800, 900];
                    
                    // Text vector positions
                    let center = p.width / 2;

                    let p1 = p.createVector(xy[p.floor(p.random(9))], xy[p.floor(p.random(9))]);
                    let p2 = p.createVector(xy[p.floor(p.random(9))], xy[p.floor(p.random(9))]);
                    let p3 = p.createVector(xy[p.floor(p.random(9))], xy[p.floor(p.random(9))]);
                    let p4 = p.createVector(xy[p.floor(p.random(9))], xy[p.floor(p.random(9))]);
                    let p5a = p.createVector(xy[p.floor(p.random(9))], xy[p.floor(p.random(9))]);
                    let p6 = p.createVector(xy[p.floor(p.random(9))], xy[p.floor(p.random(9))]);
                    let p7 = p.createVector(xy[p.floor(p.random(9))], xy[p.floor(p.random(9))]);
                    let p8 = p.createVector(xy[p.floor(p.random(9))], xy[p.floor(p.random(9))]);
                    let p9 = p.createVector(xy[p.floor(p.random(9))], xy[p.floor(p.random(9))]);
                    let p10 = p.createVector(xy[p.floor(p.random(9))], xy[p.floor(p.random(9))]);
                    let p11 = p.createVector(xy[p.floor(p.random(9))], xy[p.floor(p.random(9))]);
                    
                    // A vector positions
                    let a1 = p.createVector(300, 900);
                    let a2 = p.createVector(540, 200);
                    let a3 = p.createVector(656, 540);
                    let a4 = p.createVector(694, 640);
                    let a5 = p.createVector(780, 900);
                    let a6 = p.createVector(540, 640);

                    
                    let mover, moverTwo, moverThree;
                    
                    // Save component reference for easier access
                    const vm = this;
                    
                    // T vector positions
                    let t1 = p.createVector(340, 200);
                    let t2 = p.createVector(540, 200);
                    let t3 = p.createVector(540, 600);
                    let t4 = p.createVector(540, 680);
                    let t5 = p.createVector(540, 900);
                    let t6 = p.createVector(620, 200);
                    let t7 = p.createVector(740, 200);

                    // E vector positions
                    let e1 = p.createVector(740, 200);
                    let e2 = p.createVector(340, 200);
                    let e3 = p.createVector(340, 600);
                    let e4 = p.createVector(340, 680);
                    let e5 = p.createVector(340, 900);
                    let e6 = p.createVector(740, 900);
                    let e7 = p.createVector(440, 540);
                    let e8 = p.createVector(700, 540);

                    // K vector positions
                    let k1 = p.createVector(340, 200);
                    let k2 = p.createVector(340, 900);
                    let k3 = p.createVector(740, 200);
                    let k4 = p.createVector(440, 540);
                    let k5 = p.createVector(340, 540);
                    let k6 = p.createVector(480, 580);
                    let k7 = p.createVector(740, 900);
                    let k8 = p.createVector(800, 900);
                    
                    // N vector positions
                    let n1 = p.createVector(340, 900);
                    let n2 = p.createVector(340, 200);
                    let n3 = p.createVector(500, 200);
                    let n4 = p.createVector(680, 740);
                    let n5 = p.createVector(720, 900);
                    let n6 = p.createVector(800, 900);
                    let n7 = p.createVector(800, 180);

                    // O vector positions
                    let o1 = p.createVector(340, 200);
                    let o2 = p.createVector(740, 200);
                    let o3 = p.createVector(340, 480);
                    let o4 = p.createVector(340, 700);
                    let o5 = p.createVector(740, 480);
                    let o6 = p.createVector(740, 700);
                    let o7 = p.createVector(340, 900);
                    let o8 = p.createVector(740, 900);
                    
                    // G vector positions
                    let g1 = p.createVector(740, 200);
                    let g2 = p.createVector(340, 200);
                    let g3 = p.createVector(340, 480);

                    let g4 = p.createVector(340, 580);
                    let g5 = p.createVector(340, 900);
                    let g6 = p.createVector(740, 900);

                    let g7 = p.createVector(740, 900);
                    let g8 = p.createVector(740, 700);
                    let g9 = p.createVector(540, 700);

                    // R vector positions
                    let r1 = p.createVector(340, 900);
                    let r2 = p.createVector(340, 200);
                    let r3 = p.createVector(540, 200);

                    let r4 = p.createVector(500, 200);
                    let r5 = p.createVector(680, 650);
                    let r6 = p.createVector(680, 556);
                    let r7 = p.createVector(880, 1000);
                    let r8 = p.createVector(900, 1000);

                    // F vector positions
                    let f1 = p.createVector(340, 900);
                    let f2 = p.createVector(340, 200);
                    let f3 = p.createVector(540, 200);

                    let f4 = p.createVector(500, 200);
                    let f5 = p.createVector(680, 650);
                    let f6 = p.createVector(680, 556);
                    let f7 = p.createVector(880, 1000);
                    let f8 = p.createVector(900, 1000);

                    p.preload = function() {
                        try {
                            font = p.loadFont('/IBMPlexSans-Bold.ttf');
                            fontMono = p.loadFont('/IBMPlexMono-Regular.ttf');
                            console.log("fonts loaded");
                        } catch (err) {
                            console.error("Error loading fonts:", err);
                            font = null;
                            fontMono = null;
                        }
                    };

                    p.setup = function() {
                        console.log("Setting up canvas with dimensions:", vm.width, vm.height);
                        p.createCanvas(vm.width, vm.height);
                        
                        // Create the movers here
                        mover = createMover();
                        moverTwo = createMover();
                        moverThree = createMover();
                        
                        console.log("Canvas created with dimensions:", p.width, p.height);
                        console.log("setup initialized");
                    };
// DRAW :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::: 
                    p.draw = function() {
                        p.background(background);
                        const degree = p.frameCount * 3;
                        const y = p.sin(p.radians(degree)) * 50;
                        
                        p.push();
                        p.translate(0, p.height / 2);
                        p.noStroke();
                        p.fill(neonGreen);
                        p.ellipse(vm.posX, y, 20, 20);
                        p.pop();
                        
                        // Get current speed directly from Vue component
                        const currentSpeed = Number(vm.speed);
                        
                        // Apply speed to position
                        if (vm.speed < 0) {
                            vm.posX += vm.speed;
                        } else {
                            vm.posX += currentSpeed;
                        }

                        if (vm.posX > p.width - 10 || vm.posX < 10) {
                            vm.speed *= -1;
                        }

                        if (font) drawTxt();
                        drawGrid(10, 10);
                        
                        // Make sure movers are defined before using them
                        if (mover) {
                            mover.update();
                            mover.show();
                            mover.checkEdges();
                        }
                        
                        if (moverTwo) {
                            moverTwo.update();
                            moverTwo.show();
                            moverTwo.checkEdges();
                        }
                        
                        if (moverThree) {
                            moverThree.update();
                            moverThree.show();
                            moverThree.checkEdges();
                        }
                        
                        // capitalA().show();
                        // capitalT().show();
                        // capitalE().show();
                        // capitalK().show();
                        // capitalN().show();
                        // capitalO().show();
                        // capitalG().show();
                        capitalR().show();


                        techShit(140, 100, 3, 3, neonGreen);
                        techShit(140, 200, 3, 3, neonGreen);
                        techShit(140, 300, 3, 3, pink);
                        techShit(940, 300, 30, 10, neonGreen);
                        techShit(640, 960, 10, 6, babyBlue);
                        
                        if (fontMono) drawTxtTwo();
                        circleGrid(100, 100, 4, 40);
                        circleGrid(800, 700, 4, 10);
                        circleGrid(100, 900, 4, 16);
                    };

                    let techShit = (x, ty, w, pad, c) => {
                        p.stroke(c);
                        p.strokeWeight(2);
                        for (let i = 0; i < 10; i++) {
                            p.line(x, ty, x + w, ty);
                            ty += pad;
                        }
                    }

                    let bigCrosshair = () => {
                        p.strokeWeight(2);
                        p.stroke(neonGreen);
                        p.line(p.width / 2, 100, p.width / 2, p.height - 100);
                        p.line(100, p.height / 2, p.width - 100, p.height / 2);
                    }

                    let circleGrid = (x, y, d, num) => {
                        p.fill(bgblack);
                        p.noStroke();
                        for (let i = 0; i < num; i++) {
                            let tempX = x + (i * 4);
                            for (let j = 0; j < num; j++) {
                                p.circle(tempX, y + (j * 4), d);
                            }
                        }
                    }

                    let drawTxt = () => {
                        p.noStroke();
                        p.fill(yellow);
                        p.textFont(font);
                        p.textSize(14);
                        p.text(tgfx[0], p1.x, p1.y);
                        p.text(tgfx[1], p2.x, p2.y);
                        p.text(tgfx[2], p3.x, p3.y);
                        p.text(tgfx[3], p4.x, p4.y);
                        p.text(tgfx[4], p5a.x, p5a.y);
                        p.text(tgfx[5], p6.x, p6.y);
                        p.text(tgfx[6], p7.x, p7.y);
                        p.text(tgfx[7], p8.x, p8.y);
                        p.text(tgfx[8], p9.x, p9.y);
                        p.text(tgfx[9], p10.x, p10.y);
                        p.text(tgfx[10], p11.x, p11.y);
                    }

                    let drawTxtTwo = () => {
                        p.noStroke();
                        p.fill(purple);
                        p.textFont(fontMono);
                        p.textSize(10);
                        p.text("TGFX :: Brand Grafix", 900, 800);
                    }

                    let drawGrid = (cols, rows) => {
                        p.stroke(0);
                        p.strokeWeight(1);
                        for (let i = 1; i < cols; i++) {
                            for (let j = 1; j < rows; j++) {
                                p.line(
                                    i * p.width / cols, 
                                    p.width / cols, 
                                    i * p.width / cols, 
                                    p.height - p.width / cols
                                );
                                p.line(
                                    p.height / rows, 
                                    j * p.height / rows, 
                                    p.width - p.height / rows, 
                                    j * p.height / rows
                                );
                            }
                        }
                    }
                    
                    let createMover = () => {
                        return {
                            position: p.createVector(p.random(p.width), p.random(p.height)),
                            velocity: p.createVector(p.random(-2, 2), p.random(-2, 2)),
                            update: function() {
                                this.position.add(this.velocity);
                            },
                            show: function() {
                                p.noStroke();
                                p.fill(p.random(colors));
                                p.ellipse(this.position.x, this.position.y, 20, 20);
                            },
                            checkEdges: function() {
                                if (this.position.x > p.width) {
                                    this.position.x = 0;
                                } else if (this.position.x < 0) {
                                    this.position.x = p.width;
                                }

                                if (this.position.y > p.height) {
                                    this.position.y = 0;
                                } else if (this.position.y < 0) {
                                    this.position.y = p.height;
                                }
                            }
                        };
                    }

                    let capitalA = () => {
                        return {
                            show: function(){
                                let gradient = p.drawingContext.createLinearGradient(300, 900, 700, 200);
                                p.noFill();
                                p.strokeWeight(vm.weight);
                                p.strokeJoin(p.ROUND);
                                p.strokeCap(p.ROUND);
                                
                                gradient.addColorStop(0, yellow);
                                gradient.addColorStop(0.5, orange);
                                gradient.addColorStop(1, babyBlue);

                                p.drawingContext.strokeStyle = gradient;
                                p.drawingContext.beginPath();
                                p.drawingContext.moveTo(a1.x, a1.y);
                                p.drawingContext.lineTo(a2.x, a2.y);
                                p.drawingContext.lineTo(a3.x, a3.y);
                                p.drawingContext.stroke();
                                p.drawingContext.closePath();

                                p.strokeWeight(60);
                                p.drawingContext.strokeStyle = pink;
                                p.drawingContext.beginPath();
                                p.drawingContext.moveTo(a4.x, a4.y);
                                p.drawingContext.lineTo(a5.x, a5.y);
                                p.drawingContext.stroke();
                                p.drawingContext.closePath();
                                if (vm.weight > 186) {
                                    p.fill(bgblack);
                                } else {
                                    p.fill(babyBlue);
                                }
                                p.circle(a6.x, a6.y, 100); 
                            }
                        }
                    }

                    let capitalT = () => {
                        return {
                            show: function() {
                                let gradient = p.drawingContext.createLinearGradient(300, 900, 700, 200);
                                p.noFill();
                                p.strokeWeight(vm.weight);
                                p.strokeJoin(p.ROUND);
                                p.strokeCap(p.ROUND);
                                
                                gradient.addColorStop(0, yellow);
                                gradient.addColorStop(0.5, orange);
                                gradient.addColorStop(1, babyBlue);

                                p.drawingContext.strokeStyle = gradient;
                                p.drawingContext.beginPath();
                                p.drawingContext.moveTo(t1.x, t1.y);
                                p.drawingContext.lineTo(t2.x, t2.y);
                                p.drawingContext.lineTo(t3.x, t3.y);
                                p.drawingContext.stroke();
                                p.drawingContext.closePath();

                                p.strokeWeight(60);
                                p.drawingContext.strokeStyle = pink;
                                p.drawingContext.beginPath();
                                p.drawingContext.moveTo(t4.x, t4.y);
                                p.drawingContext.lineTo(t5.x, t5.y);
                                p.drawingContext.stroke();
                                p.drawingContext.closePath();

                                p.strokeWeight(60);
                                p.drawingContext.strokeStyle = purple;
                                p.drawingContext.beginPath();
                                p.drawingContext.moveTo(t6.x, t6.y);
                                p.drawingContext.lineTo(t7.x, t7.y);
                                p.drawingContext.stroke();
                                p.drawingContext.closePath();

                                console.log(p.width / 2 - 200);
                                console.log(t1.x);
                            }
                        }
                    }

                    let capitalE = () => {
                        return {
                            show: function() {
                                let gradient = p.drawingContext.createLinearGradient(300, 900, 700, 200);
                                p.noFill();
                                p.strokeWeight(vm.weight);
                                p.strokeJoin(p.ROUND);
                                p.strokeCap(p.ROUND);
                                
                                gradient.addColorStop(0, yellow);
                                gradient.addColorStop(0.5, orange);
                                gradient.addColorStop(1, babyBlue);

                                p.drawingContext.strokeStyle = gradient;
                                p.drawingContext.beginPath();
                                p.drawingContext.moveTo(e1.x, e1.y);
                                p.drawingContext.lineTo(e2.x, e2.y);
                                p.drawingContext.lineTo(e3.x, e3.y);
                                p.drawingContext.stroke();
                                p.drawingContext.closePath();

                                p.strokeWeight(60);
                                p.drawingContext.strokeStyle = pink;
                                p.drawingContext.beginPath();
                                p.drawingContext.moveTo(e4.x, e4.y);
                                p.drawingContext.lineTo(e5.x, e5.y);
                                p.drawingContext.lineTo(e6.x, e6.y);
                                p.drawingContext.stroke();
                                p.drawingContext.closePath();

                                p.strokeWeight(60);
                                p.strokeCap(p.SQUARE);
                                p.drawingContext.strokeStyle = purple;
                                p.drawingContext.beginPath();
                                p.drawingContext.moveTo(e7.x, e7.y);
                                p.drawingContext.lineTo(e8.x, e8.y);
                                p.drawingContext.stroke();
                                p.drawingContext.closePath();
                                p.strokeCap(p.ROUND); // reset to round
                            }
                        }
                    }

                    let capitalK = () => {
                        return {
                            show: function() {
                                let gradient = p.drawingContext.createLinearGradient(300, 900, 700, 200);
                                p.noFill();
                                p.strokeWeight(vm.weight);
                                p.strokeJoin(p.ROUND);
                                p.strokeCap(p.ROUND);
                                
                                gradient.addColorStop(0, yellow);
                                gradient.addColorStop(0.5, orange);
                                gradient.addColorStop(1, babyBlue);

                                p.drawingContext.strokeStyle = gradient;
                                p.drawingContext.beginPath();
                                p.drawingContext.moveTo(k1.x, k1.y);
                                p.drawingContext.lineTo(k2.x, k2.y);
                                p.drawingContext.stroke();
                                p.drawingContext.closePath();

                                p.strokeWeight(60);
                                p.drawingContext.strokeStyle = pink;
                                p.drawingContext.beginPath();
                                p.drawingContext.moveTo(k3.x, k3.y);
                                p.drawingContext.lineTo(k4.x, k4.y);
                                p.drawingContext.lineTo(k5.x, k5.y);
                                p.drawingContext.stroke();
                                p.drawingContext.closePath();

                                p.strokeWeight(60);
                                p.strokeCap(p.SQUARE);
                                p.drawingContext.strokeStyle = purple;
                                p.drawingContext.beginPath();
                                p.drawingContext.moveTo(k6.x, k6.y);
                                p.drawingContext.lineTo(k7.x, k7.y);
                                p.drawingContext.lineTo(k8.x, k8.y);
                                p.drawingContext.stroke();
                                p.drawingContext.closePath();
                                p.strokeCap(p.ROUND); // reset to round
                            }
                        }
                    }
                    
                    let capitalN = () => {
                        return {
                            show: function() {
                                let gradient = p.drawingContext.createLinearGradient(300, 900, 700, 200);
                                p.noFill();
                                p.strokeWeight(vm.weight);
                                p.strokeJoin(p.ROUND);
                                p.strokeCap(p.ROUND);
                                
                                gradient.addColorStop(0, yellow);
                                gradient.addColorStop(0.5, orange);
                                gradient.addColorStop(1, babyBlue);

                                p.drawingContext.strokeStyle = gradient;
                                p.drawingContext.beginPath();
                                p.drawingContext.moveTo(n1.x, n1.y);
                                p.drawingContext.lineTo(n2.x, n2.y);
                                p.drawingContext.lineTo(n3.x, n3.y);
                                p.drawingContext.lineTo(n4.x, n4.y);
                                p.drawingContext.stroke();
                                p.drawingContext.closePath();

                                p.strokeWeight(30);
                                p.drawingContext.strokeStyle = babyBlue;
                                p.drawingContext.beginPath();
                                p.drawingContext.moveTo(n5.x, n5.y);
                                p.drawingContext.lineTo(n6.x, n6.y);
                                p.drawingContext.lineTo(n7.x, n7.y);
                                p.drawingContext.stroke();
                                p.drawingContext.closePath();
                            }
                        }
                    }

                    let capitalG = () => {
                        return {
                            show: function() {
                                let gradient = p.drawingContext.createLinearGradient(300, 900, 700, 200);
                                p.noFill();
                                p.strokeWeight(vm.weight);
                                p.strokeJoin(p.ROUND);
                                p.strokeCap(p.ROUND);
                                
                                gradient.addColorStop(0, yellow);
                                gradient.addColorStop(0.5, orange);
                                gradient.addColorStop(1, babyBlue);

                                p.drawingContext.strokeStyle = gradient;
                                p.drawingContext.beginPath();
                                p.drawingContext.moveTo(g1.x, g1.y);
                                p.drawingContext.lineTo(g2.x, g2.y);
                                p.drawingContext.lineTo(g3.x, g3.y);
                                p.drawingContext.stroke();
                                p.drawingContext.closePath();

                                p.strokeWeight(3);
                                p.drawingContext.strokeStyle = neonGreen;
                                p.drawingContext.beginPath();
                                p.drawingContext.moveTo(g4.x, g4.y);
                                p.drawingContext.lineTo(g5.x, g5.y);
                                p.drawingContext.lineTo(g6.x, g6.y);
                                p.drawingContext.stroke();
                                p.drawingContext.closePath();

                                p.strokeWeight(30);
                                p.drawingContext.strokeStyle = babyBlue;
                                p.drawingContext.beginPath();
                                p.drawingContext.moveTo(g7.x, g7.y);
                                p.drawingContext.lineTo(g8.x, g8.y);
                                p.drawingContext.lineTo(g9.x, g9.y);
                                p.drawingContext.stroke();
                                p.drawingContext.closePath();
                            }
                        }
                    }

                    let capitalR = () => {
                        return {
                            show: function() {
                                let gradient = p.drawingContext.createLinearGradient(300, 900, 700, 200);
                                p.noFill();
                                p.strokeWeight(vm.weight);
                                p.strokeJoin(p.ROUND);
                                p.strokeCap(p.ROUND);
                                
                                gradient.addColorStop(0, yellow);
                                gradient.addColorStop(0.5, orange);
                                gradient.addColorStop(1, babyBlue);

                                p.drawingContext.strokeStyle = gradient;
                                p.drawingContext.beginPath();
                                p.drawingContext.moveTo(r1.x, r1.y);
                                p.drawingContext.lineTo(r2.x, r2.y);
                                p.drawingContext.lineTo(r3.x, r3.y);
                                p.drawingContext.stroke();
                                p.drawingContext.closePath();

                                // arc top
                                p.strokeWeight(vm.weight);
                                p.drawingContext.strokeStyle = gradient;
                                p.drawingContext.beginPath();
                                p.drawingContext.arc(540, 400, 200, p.PI/2, 0);
                                p.drawingContext.stroke();
                                p.drawingContext.closePath();

                                p.strokeWeight(30);
                                p.drawingContext.strokeStyle = purple;
                                p.drawingContext.beginPath();
                                p.drawingContext.moveTo(r5.x, r5.y);
                                p.drawingContext.lineTo(r6.x, r6.y);
                                p.drawingContext.lineTo(r7.x, r7.y);
                                p.drawingContext.lineTo(r8.x, r8.y);
                                p.drawingContext.stroke();
                                p.drawingContext.closePath();
                            }
                        }
                    }

                    let capitalO = () => {
                        return {
                            show: function() {
                                let gradient = p.drawingContext.createLinearGradient(300, 900, 700, 200);
                                p.noFill();
                                p.strokeWeight(vm.weight);
                                p.strokeJoin(p.ROUND);
                                p.strokeCap(p.ROUND);
                                
                                gradient.addColorStop(0, yellow);
                                gradient.addColorStop(0.5, orange);
                                gradient.addColorStop(1, babyBlue);
                                
                                p.strokeWeight(10);
                                p.drawingContext.strokeStyle = pink;
                                p.drawingContext.beginPath();
                                p.drawingContext.moveTo(o3.x, o3.y);
                                p.drawingContext.lineTo(o4.x, o4.y);
                                p.drawingContext.stroke();
                                p.drawingContext.closePath();
                                
                                p.strokeWeight(10);
                                p.drawingContext.strokeStyle = neonGreen;
                                p.drawingContext.beginPath();
                                p.drawingContext.moveTo(o5.x, o5.y);
                                p.drawingContext.lineTo(o6.x, o6.y);
                                p.drawingContext.stroke();
                                p.drawingContext.closePath();
                                
                                // arc top
                                p.strokeWeight(vm.weight);
                                p.drawingContext.strokeStyle = gradient;
                                p.drawingContext.beginPath();
                                p.drawingContext.arc(540, 440, 200, p.PI, 0);
                                p.drawingContext.stroke();
                                p.drawingContext.closePath();

                                // arc bottom
                                p.strokeWeight(vm.weight);
                                p.drawingContext.strokeStyle = gradient;
                                p.drawingContext.beginPath();
                                p.drawingContext.arc(540, 740, 200, 0, p.PI);
                                p.drawingContext.stroke();
                                p.drawingContext.closePath();
                            }
                        }
                    }
                }, container);
            }
        },
        watch: {
            // Watch for speed changes and redraw if needed
            speed(newVal, oldVal) {
                console.log("Speed changed from", oldVal, "to", newVal);
            },

            weight(newVal, oldVal) {
                console.log("Weight changed from", oldVal, "to", newVal);
            }
        }
    };
</script>

<style scoped>
  .canvas-container {
    display: block;
    margin: 0 auto;
    padding: 0;
    /* border-radius: 20px; */
    overflow: hidden;
    width: 1080px;
    height: 1080px;
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
  
  .speed-display {
    margin-top: 10px;
    font-family: monospace;
    max-width: min-content;
  }
</style>