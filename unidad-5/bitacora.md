
# Evidencias de la unidad 5

## Actividad 1

1. Describe cómo se están comunicando el micro:bit y el sketch de p5.js. ¿Qué datos envía el micro:bit?
   
    El microbit envía el valor en X, en Y y dos falsos o verdaderos dependiendo si se presionaron o no los botones A y B.
   
2. ¿Cómo es la estructura del protocolo ASCII usado?
   
    Cada grupo de datos es "(numero de X) , (numero de Y) , (estado Boton A) , (estado Boton B) \n"
Separa cada dato con una coma y avisa que ese grupo de datos terminó con un salto de línea.

3. Muestra y explica la parte del código de p5.js donde lee los datos del micro:bit y los transforma en coordenadas de la pantalla.
   
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

4. ¿Cómo se generan los eventos A pressed y B released que se generan en p5.js a partir de los datos que envía el micro:bit?

    Cada vez que llegan datos del microbit las variables se actualizan y se comparan con el estado anterior.
```js
microBitAState=values[2].toLowerCase()==="true";
microBitBState=values[3].toLowerCase()==="true";
updateButtonStates(microBitAState,microBitBState);
```
   y gracias a esa comparación se puede saber si se reliazo una transcición que genera un evento, con el boton A debe pasar de no presionado a presionado y con el boton B pasa de presionado a no presionado/soltado, y ya luego se hace la accion que se le fue correspondido a cada boton.  
   
5. Capturas de pantalla de los algunos dibujos que hayas hecho con el sketch.  

 ![Imagen 1](https://github.com/user-attachments/assets/c482d4d1-a4c2-45ea-b27b-e2d9633f3733)
 ![Imagen 2](https://github.com/user-attachments/assets/a258a3ed-2186-45e3-95b1-a7202f9ab4ab)
 ![Imagen 3](https://github.com/user-attachments/assets/cc0ca0b1-7c4b-4f43-90ba-40394f2d4e37)

## Actividad 2 

##### Primer código:

a) Datos del SeriaTerminal como texto:  

<img width="880" height="157" alt="1 1" src="https://github.com/user-attachments/assets/e43b36b6-4ba1-49f3-93b1-c3889905720e" />  

b) Datos del SerialTerminal como hex:  

<img width="869" height="150" alt="2 1" src="https://github.com/user-attachments/assets/fa7fe49c-64fd-405c-99e3-9fe49b614bc6" />  

- ¿Qué ventajas y desventajas ves en usar un formato binario en lugar de texto en ASCII? 
    Una ventaja es que el paquete de datos es mucho mas corto que en ASCII y puede ser un poco mas facil en la lectura de los datos (esto viendo los datos como hex), la desventaja es que en formato de texto no se entiende nada.

##### Segundo código:

a) Datos del SeriaTerminal como texto:  

<img width="663" height="25" alt="1" src="https://github.com/user-attachments/assets/9a0508a7-480c-407b-b5a5-560b9bea9ddd" />  


b) Datos del SerialTerminal como hex:  

<img width="885" height="33" alt="2" src="https://github.com/user-attachments/assets/957b3eec-fc8c-453b-93bd-cd5780e095d7" />  


- ¿Cuántos bytes se están enviando por mensaje? ¿Cómo se relaciona esto con el formato '>2h2B'? ¿Qué significa cada uno de los bytes que se envían?
=  
- Recuerda de la unidad anterior que es posible enviar números positivos y negativos para los valores de xValue y yValue. ¿Cómo se verían esos números en el formato '>2h2B'?
= 
##### Tercer código:
<img width="164" height="92" alt="3" src="https://github.com/user-attachments/assets/718190a6-c25e-4177-ac71-98405d317380" />  

- ¿Qué diferencias ves entre los datos en ASCII y en binario?
    En binario realmente no se entiende mucho el contenido de los datos, en ASCII si se logra comprender. (En texto)

## Actividad 3

- Por qué en la unidad anterior teníamos que enviar la información delimitada y además marcada con un salto de línea y ahora no es necesario?
  
    Porque ahora el paquete de datos es mas corto y no contiene tanta informacion, es decir, no es algo muy largo con muchos numeros que me arman otros valores, ahora son pocos.

- Compara el código de la unidad anterior relacionado con la recepción de los datos seriales que ves ahora. ¿Qué cambios observas?
   
    Ya no se guarda cada dato en un espacio, sino que ha las coordenadas de X y Y se les da como dos espacios, esto supongo que es porque a esos datos se les dan dos bytes.

- Analiza el código, observa los cambios. Ejecuta y luego observa la consola. ¿Qué ves?
   
    Se envian siempre los mismos valores.

- ¿Qué cambios tienen los programas y ¿Qué puedes observar en la consola del editor de p5.js?
   
    Primero claramente cambia la forma en la que se reciben y se organizan los valores, se necesita "mucho" mas código para los valores binarios que para los valores es ASCII.
Ahora en la consola veo todo el tiempo que valores está recibiendo la aplicación.

![20250917_150019](https://github.com/user-attachments/assets/a204aa5c-4c3f-4d9a-a3a0-74aedbfcc8af)

## Actividad 4

[Link nueva aplicacion](https://editor.p5js.org/mariflorez06/sketches/AfCMq7qva)

## Nota

Mi nota propuesta: 3.45

1. Profundidad en la indagacion: En desarrollo (3.4), respondi las preguntas que habian durante las actividades, pero me hicieron falta algunas que no sabia muy bien como responder.
2. Calidad de la experimentacion: En desarrollo (3.4), realice los experimentos que me indicaban las actividades sin ir mucho mas alla.
3. Analisis y reflexion: Logrado (3.6), escribi y coloque imagenes en mi bitacora que corresponde a los indicado en cada actividad, pero no realice mucha explicacion teorica.
4. Apropiacion y articulacion de conceptos: En desarrollo (3.4), los conceptos estan explicados de manera muy basica.


