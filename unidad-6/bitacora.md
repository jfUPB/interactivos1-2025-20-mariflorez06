# Evidencias de la unidad 6

## Actividad 1

a. ¿Qué ocurrió en la terminal cuando ejecutaste npm install? ¿Cuál crees que es su propósito?
= Aparecio un mensaje que decia que se habian agregado 120 paquetes y se auditaron 121 paquetes en 3 segundos. Informa cuantos paquetes se descargaron y si se encontraron vulnerabilidades de seguridad.

b. ¿Qué mensaje específico apareció en la terminal después de ejecutar npm start? ¿Qué indica este mensaje?
```
> nodejs-test-1@1.0.0 start
> node server.js

Server is listening on http://localhost:3000
```
La primer linea es el nombre y la version del proyecto. Start indica que el script esta corriendo.
La segunda linea indica que el comando se ejecuta realmente, en este caso esta corriendo server.js con Node.js.
La tercer y ultima linea, significa que el servidor esta activo, escuchando peticiones en el puerto 3000 de la computadora, si se abre esta url en un navegador, se ve la respuesta que node esta dando.

c. Describe lo que ves inicialmente en page1 y page2 en tu navegador.
= Se ven dos circulos rojos (cada uno en una page diferente), con un contorno grueso en color gris oscuro, en la mitad del circulo se crea una especie de cuerda que se une al circulo de la otra poage.

d. ¿Qué mensajes aparecieron en la terminal del servidor cuando abriste page1 y page2?
= Aparece que un usuario se conecto y muestra el ID, luego da unas coordenadas (creo que de la ventana que se abrio). Luego hay un debug que dice cuantos clientes estan conectados, si page 1 y 2 estan abiertas o cerradas; y si estan sincronizadas o no. En general, verdadero = 1, falso = 0. Luego aparece el estatus de sincronizacion, donde dice el estado de las pages, el estado de la sincronizacion y la cantidad de clientes.

e. Describe qué sucede en ambas páginas del navegador cuando mueves una de las ventanas. ¿Cambia algo visualmente? ¿Qué mensajes aparecen (si los hay) en la consola del navegador (usualmente accesible con F12 -> Pestaña Consola) y en la terminal del servidor?
= Al mover las ventanas lo unico que se mueve es la "cuerda" que une ambos circulos y en la terminal cambian los valores de X y Y.

## Actividad 2 

a. Piensa en cómo te conectas a Internet en casa o en la Universidad. 
= Si mi computador es el vehiculo, debe haber una carretera que me conecte al internet. Supongo que al instalar un servicio de wifi en casa, es un medio que me comienza a conectar a esa carretera que me lleva hasta el internet.

b. ¿Puedes identificar otros ejemplos de relaciones Cliente-Servidor en tu vida diaria?
= Al pedir un servicio en una app de transportes, yo soy el cliente y la persona que maneja el vehiculo es el servidor; yo pido que me lleven a un lugar y me entregan llevandome al lugar. Al sacar a mi perra a hacer sus necesidades, mi perra es el cliente y yo soy el servidor; ella pide salir para hacer sus necesidades y yo le entrego la salida. 

c. Toma la URL de tu sitio web favorito. Intenta identificar el protocolo, el nombre de dominio y la ruta (si la hay). ¿Qué crees que pasa si solo escribes el nombre de dominio (ej. www.google.com) sin una ruta específica? ¿Qué “página por defecto” crees que te envía el servidor?
= https://www.youtube.com/watch?v=2z4_4uJq20E&t=1298s, (https://) Protocolo, (www.youtube.com) Nombre de Dominio, (watch?v=2z4_4uJq20E&t=1298s) Ruta Especifica, en este caso un video.
Si pongo www.youtube.com sin ninguna ruta, me lleva al inicio de la pagina.

d. Compara HTTP con los protocolos seriales que usaste.
= **SIMILITUDES:** Todos transmiten datos, usan bytes y tienen reglas. **DIFERENCIAS:** https es mucho mas complejo, ASCII es muy simple pues cada byte es un caracter, Binario es muy poco legible para humanos.
HTTP necesita ser mas complejo puesto que da un lenguaje mas estructurado con contexto y significado, para que la comunicacion sea mas clara, segura y flexible.

e. Piensa en una página web simple, como un formulario de login.
1) ¿Qué parte crees que es HTML (ej. los campos de texto, el botón)? = El titulo que dice en que pagina estas, el subtitulo que dice que vas a hacer, y puede haber un parrafo explicativo que diga porque necesitas tu login o algo asi. Ademas tiene los botones donde se debe ingresar la informacion (correo y password) y el de continuar o ingresar.
2) ¿Qué parte es CSS (ej. el color del botón, el tipo de letra)? = De que color es el fondo, las fuentes de todas las letras y sus colores, el color del boton de continuar.
3) ¿Qué parte es JavaScript (ej. la comprobación de si escribiste algo antes de enviar, el mensaje de “contraseña incorrecta” que aparece sin recargar la página)? = verificar que en el correo si se este copiando una direccion de correo y no cualquier cosa, verificar si la contraseña es incorrecta, verificar si el correo si tiene un usario creado en la plataforma.

f. Compara el bucle draw() de p5.js con este modelo de “esperar a que algo pase y reaccionar”.
1) ¿Qué ventajas crees que tiene el modelo basado en eventos para una interfaz de usuario web? = Que al estar esperando un evento, la pagina va a pesar tanto porque no estara haciendo frecuentemente algo, sino que esta esperando a.
2) ¿Sería eficiente tener un bucle draw() redibujando toda la página 60 veces por segundo si nada ha cambiado? = En este caso, una interfaz de usuario web, no es muy eficiente y consumira mas.

g. ¿Por qué crees que podría ser útil usar JavaScript tanto en el cliente (navegador) como en el servidor? ¿Se te ocurre alguna ventaja para los desarrolladores? = Supongo que es mas facil escribir en el lenguaje que los otros leen, es como tener un show con un publico de habla hispana y hablar español, a tener un show con un publico gringo y hablar chino; es confunso tanto para el cliente como para el servidor y necesitaria pasos de mas para poder comprender.

h. Resume con tus propias palabras la diferencia fundamental entre una comunicación HTTP tradicional y una comunicación usando WebSockets/Socket.IO. ¿En qué tipo de aplicaciones has visto o podrías imaginar que se usa esta comunicación en tiempo real? = La comunicacion tradicional de http es como querer comunicarme con alguien que esta lejos y que mi medio de comunicacion sean correos, y que tengamos que mandar un correo cada vez que queremos comunicar algo. En cambio los WebSockets es como comunicarme por mensajes de whatsapp.
Creo que Whatsapp, instagram, telegram, etc, utilizan este ultimo metodo.

## Actividad 3 

### Experimento 1
Al acceder a http://localhost:3000/pagina_uno dice que "no se puede obtener", pero al acceder a http://localhost:3000/page1 lo hace con normalidad. Supongo que es porque el codigo espera que la ruta especifica sea page1 y no pagina_uno, entonces el Js salta un error o simplemente no carga.

### Experimento 2
Page 1, ID: _kwMdaqEQr1krou2AAAF
Page 2, ID: _H31ZNCzRnvCs4P7AAAH
Si coincide el ID luego de cerrar page 1. Si coincide el ID luego de cerrar page 2.

### Experimento 3
Datos Mov. Page1: win1update from ID: CfYDkdRreSNBEv2bAAAJ Data: { x: 462, y: 160, width: 575, height: 206 }
Datos Mov. Page2: win2update from ID: Y9BanCRJgmVGOopAAAAL Data: { x: 609, y: 529, width: 576, height: 206 }
Quitando broadcast: Ahora no aparece la cuerda de page1 e igual se sigue actualizando win1update

### Experimento 4
Port = 3001: Dice que esta escuchando en el puerto 3001
Al acceder a http://localhost:3000/page1, la pagina no carga y dice que no se puede acceder a ese sitio.
Al acceder a http://localhost:3001/page1, no pasa nada, accede normal

## Actividad 4

### Experimento 1
Si, sale un error de conexion: ERR_CONNECTION_REFUSED.
Si, desaparecen los errores. Dice que esta conectada con un ID, que el estatus de sincronizacion es no sincronizado, recibe datos remotos de X,Y,Widht y Height.

### Experimento 2 
Ahora al mover el page2 no cambian los datos, no esta realizando un update por lo que comentamos la linea que lo hacia. Ademas tambien noto que la cuerda de page2 sigue de manera correcta a page1, pero page1 no sigue bien a page2, es como si siempre estuviera en la misma parte.

### Experimento 3
Al mover page1 se actualizan los datos en la consola de page2. Pero al mover page2 quedan igual, debe ser por haber comentado en el codigo la linea que actualiza page2.

### Experimento 4
Asi modifique el if
```js
 if ( true//currentPageData.x !== previousPageData.x || currentPageData.y !== previousPageData.y || 
        //currentPageData.width !== previousPageData.width || currentPageData.height !== previousPageData.height
        ) {

        console.log("El if se ejecuto");    
        point2 = [currentPageData.width / 2, currentPageData.height / 2]
        socket.emit('win2update', currentPageData, socket.id);
        previousPageData = currentPageData; 
    }
```
La consola de page2 no para de mandar datos actualizando la ubicacion de page2 incluso sin haberla movida, y la consola de page1 solo se modifica si se mueve esta ventana.

### AutoEvaluacion
(3) realice 4 actividades completas.
En todas las actividades se evidencia como trate de comprender los temas en su totalidad [Por ejemplo](https://github.com/jfUPB/interactivos1-2025-20-mariflorez06/edit/unidad6/apply/unidad-6/bitacora.md#actividad-1-actividad-1), supe crear ejemplos de los conceptos con cosas de la vida cotidiana [Por ejemplo](https://github.com/jfUPB/interactivos1-2025-20-mariflorez06/edit/unidad6/apply/unidad-6/bitacora.md#actividad-2), realice todos los experimentos documentando lo que veia o sucedia en cada uno de ellos [Por ejemplo](https://github.com/jfUPB/interactivos1-2025-20-mariflorez06/edit/unidad6/apply/unidad-6/bitacora.md#actividad-3-actividad-3).



