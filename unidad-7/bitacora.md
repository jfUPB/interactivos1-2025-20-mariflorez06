# Evidencias de la unidad 7 

## Fase Set 💡

### Actividad 1

a) ¿Qué URL de Dev Tunnels obtuviste? ¿Por qué crees que necesitamos usar esta URL en lugar de http://localhost:3000 o la IP local de tu computador para que el celular se conecte?  

  = Obtuve esta URL https://2pv40hxr-3000.use2.devtunnels.ms/. Creo que se necesita una diferente puesto que no vamos a concetarnos desde el mismo dispositivo sino desde dos diferentes; además al intentar acceder con el localhost al usar el /mobile, no deja acceder a la aplicación.

b) Describe brevemente qué hace npm install y npm start.  

  = npm install, instala todos los paquetes que necesitan y npm start, inicia la aplicación y da la url.

c) ¿Qué mensajes observaste en la terminal del servidor al conectar el cliente de escritorio y el cliente móvil? ¿Eran diferentes los mensajes o identificadores?  

  = No, los mensajes eran iguales, New client connected, para ambos dispositivos.

d) Describe el comportamiento observado: ¿Funcionó la interacción? ¿Hubo algún retraso (latencia)?  

  = La interacción funcionó, al inicio, el primer movimiento quizas tiene un poco de delay pero de resto todo funciona al tiempo.

## Fase Seek 🔎

### Actividad 2

a) Explica con tus propias palabras: ¿Por qué es necesario Dev Tunnels en este escenario y cómo funciona conceptualmente?  

  = Es necesario porque necesitamos que la aplicación funcione en dos dispositivos a la vez, si solo se quiere usar el localhost solo se puede utilizar desde, por ejemplo, dos ventanas del computador. En cambio, teniendo un puerto si podemos utilizar el computador y el celular, ya que funciona como un tunel para el celular llevando los datos que el recbe hasta el localhost en el computador. Conceptualmete funciona como un medio de comunicación entre el computador y el celular.

b) Describe la función de touchMoved() y por qué se usa la variable threshold en el cliente móvil.  

  = touchMoved() es la función que va a leer los touch del celular (o del mouse del computador), dandole variales de mouseX y mouseY; el threshold sirve como un minimo, ya que comparamos este minimo con la nueva posicion del movimiento y si es significativo, se redibujará el circulo en la nueva posición.

c) Compara brevemente Dev Tunnels con simplemente usar la IP local. ¿Cuáles son las ventajas y desventajas de cada uno?

**Dev Tunnels:** Se puede acceder desde cualquier lugar con internet, Es de menor velocidad, Se puede probar desde cualquier dispositivo.

**IP Local:** Solo funciona dentro de la misma red o equipo, Muy rapida, Solo si el dispositivo esta en la misma red y usas la IP local

d) Coloca en tu bitácora capturas de pantalla del sistema completo funcionando. Esto lo puedes hacer abriendo tanto el mobile como el desktop en tu computador y tomando una captura de pantalla de todos los involucrados (celular, computador y terminal).

https://github.com/user-attachments/assets/0e8265ae-49ba-4b11-9814-39ea476170ff
https://github.com/user-attachments/assets/4be3dcbd-9665-4719-b885-cfd523f8d328

### Actividad 3

a) ¿Cuál es la función principal de express.static(‘public’) en este servidor?
  = 

b) Explica detalladamente el flujo de un mensaje táctil: 
  *¿Qué evento lo envía desde el móvil? =* socket.**emit**('message', payload).
  *¿Qué evento lo recibe el servidor? =* **socket.on**('message',(message) => { ... } ).
  *¿Qué hace el servidor con él? =* console.log('Received message =>', message); -> Imprime el mensaje. socket.broadcast.emit('message', message); -> Reenvia el mensaje a los demas clientes.
  *¿Qué evento lo envía el servidor al escritorio? =* 


