
# Evidencias de la unidad 5

## Actividad 1

#### 1. Describe cómo se están comunicando el micro:bit y el sketch de p5.js. ¿Qué datos envía el micro:bit?
   
   = El microbit envía el valor en X, en Y y dos falsos o verdaderos dependiendo si se presionaron o no los botones A y B.
   
#### 2. ¿Cómo es la estructura del protocolo ASCII usado?
   
   = Cada grupo de datos es "(numero de X) , (numero de Y) , (estado Boton A) , (estado Boton B) \n"
Separa cada dato con una coma y avisa que ese grupo de datos terminó con un salto de línea.

#### 3. Muestra y explica la parte del código de p5.js donde lee los datos del micro:bit y los transforma en coordenadas de la pantalla.
   =
```js
if(port.availableBytes()>0) {
    let data=port.readUntil("\n");
    if(data) {
      data=data.trim();
      let values=data.split(",");
      if(values.length==4) {
        microBitX=int(values[0])+windowWidth/2;
        microBitY=int(values[1])+windowHeight/2;
        microBitAState=values[2].toLowerCase()==="true";
        microBitBState=values[3].toLowerCase()==="true";
        updateButtonStates(microBitAState,microBitBState);      
} else{
        print("No se están recibiendo 4 datos del micro:bit");
      }    
   }  
}
```
Basicamente lo que lee son los datos previos que se le asignaron al microbit que mandara, es decir, xValue, yValue, aState, bState, que estan todos separadas por una coma (asi también lo lee el p5.js por esta linea let values=data.split(","); ) y cada grupo de datos termina en un salto de linea "\n". Y va poniendo en orden los datos.
Los valores de X y Y se convierten en enteros y se centran en el canvas de p5.js sumando windowWidth/2 y windowHeight/2.  

#### 4. ¿Cómo se generan los eventos A pressed y B released que se generan en p5.js a partir de los datos que envía el micro:bit?

= Cada vez que llegan datos del microbit las variables se actualizan y se comparan con el estado anterior.
```js
microBitAState=values[2].toLowerCase()==="true";
microBitBState=values[3].toLowerCase()==="true";
updateButtonStates(microBitAState,microBitBState);
```
y gracias a esa comparación se puede saber si se reliazo una transcición que genera un evento, con el boton A debe pasar de no presionado a presionado y con el boton B pasa de presionado a no presionado/soltado, y ya luego se hace la accion que se le fue correspondido a cada boton.  
#### 5. Capturas de pantalla de los algunos dibujos que hayas hecho con el sketch.
 ![Imagen 1](https://github.com/user-attachments/assets/c482d4d1-a4c2-45ea-b27b-e2d9633f3733)
 ![Imagen 2](https://github.com/user-attachments/assets/a258a3ed-2186-45e3-95b1-a7202f9ab4ab)
 ![Imagen 3](https://github.com/user-attachments/assets/cc0ca0b1-7c4b-4f43-90ba-40394f2d4e37)

## Actividad 2 


