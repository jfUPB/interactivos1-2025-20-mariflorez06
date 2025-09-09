
# Evidencias de la unidad 4

## Código

[Enlace a la aplicación a modificar](http://www.generative-gestaltung.de/2/sketches/?01_P/P_1_1_2_01)

Código a modificar:

``` js
// P_1_1_2_01
//
// Generative Gestaltung – Creative Coding im Web
// ISBN: 978-3-87439-902-9, First Edition, Hermann Schmidt, Mainz, 2018
// Benedikt Groß, Hartmut Bohnacker, Julia Laub, Claudius Lazzeroni
// with contributions by Joey Lee and Niels Poldervaart
// Copyright 2018
//
// http://www.generative-gestaltung.de
//
// Licensed under the Apache License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License.
// You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
// See the License for the specific language governing permissions and
// limitations under the License.

/**
 * changing the color circle by moving the mouse.
 *
 * MOUSE
 * position x          : saturation
 * position y          : brighness
 *
 * KEYS
 * 1-5                 : number of segments
 * s                   : save png
 */
'use strict';

var segmentCount = 360;
var radius = 300;

function setup() {
  createCanvas(800, 800);
  noStroke();
}

function draw() {
  colorMode(HSB, 360, width, height);
  background(360, 0, height);

  var angleStep = 360 / segmentCount;

  beginShape(TRIANGLE_FAN);
  vertex(width / 2, height / 2);

  for (var angle = 0; angle <= 360; angle += angleStep) {
    var vx = width / 2 + cos(radians(angle)) * radius;
    var vy = height / 2 + sin(radians(angle)) * radius;
    vertex(vx, vy);
    fill(angle, mouseX, mouseY);
  }

  endShape();
}

function keyPressed() {
  if (key == 's' || key == 'S') saveCanvas(gd.timestamp(), 'png');

  switch (key) {
  case '1':
    segmentCount = 360;
    break;
  case '2':
    segmentCount = 45;
    break;
  case '3':
    segmentCount = 24;
    break;
  case '4':
    segmentCount = 12;
    break;
  case '5':
    segmentCount = 6;
    break;
  }
}
```

[Enlace a la aplicación modificada](https://editor.p5js.org/mariflorez06/sketches/h_2UV1ArA)

Código modificado:

``` js
'use strict';

var segmentCount = 360;
var radius = 300;

let port;
let connectBtn;
let connectionInitialized = false;
let microBitConnected = false;

const STATES = {
  WAIT_MICROBIT_CONNECTION:"WAITMICROBIT_CONNECTION",
  RUNNING: "RUNNING",
};

let appState = STATES.WAIT_MICROBIT_CONNECTION;
let microBitX = 0;
let microBitY = 0;
let microBitAState = false;
let microBitBState = false;
let prevmicroBitAState = false;
let prevmicroBitBState = false;

function setup() {
  createCanvas(800, 800);
  noStroke();
  
  port = createSerial();
  connectBtn = createButton("Conectar micro:bit");
  connectBtn.position(0,0);
  connectBtn.mousePressed(connectBtnClick);
}

function connectBtnClick(){
  if (!port.opened()){
    port.open("MicroPython",115200);
    connectionInitialized = false;
  } else{
    port.close();
  }
}

function updateButtonStates(newAState,newBState){
  
  if (newAState === true && prevmicroBitAState === false){
    segmentCount = 24;  
    print("Presionaste A");
  }
  
  if (newBState === false && prevmicroBitBState === true){
    segmentCount = 6;
    print("Presionaste B");
  }
  prevmicroBitAState = newAState;
  prevmicroBitBState = newBState;
}

function draw() {
  
  if (!port.opened()){
    connectBtn.html("Conectar al micro:bit");
    microBitConnected = false;
  } else {
    microBitConnected = true;
    connectBtn.html("Desconectar");
    
    if (port.opened()&& !connectionInitialized){
      port.clear();
      connectionInitialized = true;
    }
    
    if (port.availableBytes()>0){
    let data = port.readUntil("\n");
    
    if (data){
      data = data.trim();
      let values = data.split(",");
      
      if (values.length ==4){
        microBitX = int (values[0]+windowWidth/2);
        microBitY = int (values[1]+windowHeight / 2);
        microBitAState = values[2].toLowerCase()=== "true";
        microBitBState = values[3].toLowerCase()=== "true";
        updateButtonStates(microBitAState,microBitBState);
      } else {
        print ("No se estan recibiendo 4 datos del micro:bit");
      }
     }  
    }
   }
  
  switch (appState){
    case STATES.WAIT_MICROBIT_CONNECTION:
      if (microBitConnected === true){
        print("El Microbit esta listo para dibujar");
        appState = STATES.RUNNING;
      }
    
      case STATES.RUNNING:
      
      if (microBitConnected === false){
        print ("Esperando la conección");
        cursor();
        appState = STATES.WAIT_MICROBIT_CONNECTION;
      }
      
      if (microBitAState === true){
        let x = microBitX;
        let y = microBitY;
        
        if (keyIsPressed && jeyCode === SHIFT){
          
          if (abs(clickPosX - x) > abs(clickPosY -y)){
            y = clickPosY;
          } else{
            x = clickPosX;
          }
        }
        
        
      }
  }
  colorMode(HSB, 360, width, height);
  background(360, 0, height);

  var angleStep = 360 / segmentCount;

  beginShape(TRIANGLE_FAN);
  vertex(width / 2, height / 2);

  for (var angle = 0; angle <= 360; angle += angleStep) {
    var vx = width / 2 + cos(radians(angle)) * radius;
    var vy = height / 2 + sin(radians(angle)) * radius;
    vertex(vx, vy);
    fill(angle, microBitX, microBitY);
  }

  endShape();
  
}

function keyPressed() {
  if (key == 's' || key == 'S') saveCanvas(gd.timestamp(), 'png');

  switch (key) {
  case '1':
    segmentCount = 360;
    break;
  case '2':
    segmentCount = 45;
    break;
  case '3':
    segmentCount = 24;
    break;
  case '4':
    segmentCount = 12;
    break;
  case '5':
    segmentCount = 6;
    break;
  }
}
```

## Video

[Video demostratativo](https://www.youtube.com/watch?v=ngXjKTYgKnw)


