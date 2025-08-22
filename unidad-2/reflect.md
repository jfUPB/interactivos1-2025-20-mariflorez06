# Unidad 2
## 🤔 Fase: Reflect
### Actividad 6: Autoevaluación
#### Parte 1: Recuperación de conocimiento.
##### 1. Describe con tus palabras qué es una máquina de estados. ¿Cuáles son sus cuatro componentes fundamentales que has utilizado en esta unidad?
   
   Una máquina de estados es un sistema con un número de estados finitos, sus componentes son: eventos, estados, transiciones y acciones.
##### 2. Explica por qué la técnica de máquina de estados es tan útil para gestionar la “concurrencia” (atender un temporizador y botones “al mismo tiempo”) en un dispositivo con un solo hilo de ejecución como el micro:bit. ¿Qué problema soluciona en comparación con usar funciones como sleep()?
No lo sé.
   
##### 3. Imagina que tienes que añadir una nueva funcionalidad a la bomba temporizada: si se agita (shake) el micro:bit mientras la cuenta regresiva está activa, el tiempo se reduce a la mitad. ¿Cómo modificarías tu diagrama de máquina de estados para incluir este nuevo evento y acción?
Agregaría el código que realice esa acción luego del código que espera a que pase el tiempo para decrementar la cuenta.

##### 4. Explica qué es un “vector de prueba” y por qué es una herramienta crucial para verificar que una máquina de estados funciona como se espera.
   
   Porque ayuda a ver verificar que el programa funcione de manera correcta, ya que deducimos que el código es funcional y asi podemos comprobar que si ponemos acciones o cosas por las que deberia pasar, lo haga de manera correcta. Se puede ver si hay algun error luego de hacer cierta acción o de esperar algún evento.

#### Parte 2: Reflexión sobre tu proceso.
##### 1. ¿Qué parte del diseño de la bomba temporizada te resultó más desafiante: crear el diagrama de estados (Actividad 04) o traducir ese diagrama a código MicroPython (Actividad 05)? ¿Por qué?
   
   La parte más difícil fue realizar la cuenta atrás, ya que quería utilizar el código que hemos utilizado en clase, de esperar cierto tiempo, pero no sabía como implementarlo a lo que ya tenía hecho. Fue así que terminé haciendo un ciclo FOR (que para estos casos no es funcional, ya que bloquea el sistema y no le permite hacer nada más) que al inicio también me dio problemas, pero los pude solucionar y que el tiempo se redujera.
##### 2. Describe un error o “bug” que encontraste al implementar tu programa. ¿Cómo te ayudó pensar en términos de estados, eventos y transiciones a identificar y solucionar el problema?
   
   Al pasar del estado Exploted al estado Settings pensaba que lo más lógico es que el tiempo se tenía que poner como el original, es decir, tenía que volver a 20 segundos. Entonces, simplemete copié y pegué el código que había utilizado en Init para inicializar el tiempo, al inicio de settings, pero creo un error que dejó a la pantalla mostrando constantemente el 20, si aumentaba o decrementaba mostraba el número nuevo y luego otra vez el 20. Así que entendí que lo tendría que inicializar al final de Exploted y antes de que el currentState cambiara de estado.

##### 3. El problema de la bomba era complejo. ¿Qué estrategia usaste para abordarlo? ¿Comenzaste con una versión simple y añadiste funcionalidades poco a poco?
   
   Primero en modo de lista, cree los estados que utilizaría, intenté identificar los eventos de cada uno y las acciones, luego fuí implementando cosas que harían más "dinamica" la bomba, el mostrar los números en pantalla, mostrar la calavera luego de que la bomba explote. Ya cuando tuve la lista completa, la pasé al diagrama y luego al código. Después de terminar el código modifiqué y agregué algunas cosas al diagrama original.
##### 4. Ahora que entiendes el patrón de máquina de estados, ¿En qué otro tipo de proyecto o sistema de entretenimiento digital crees que podrías aplicarlo?
   
   No lo sé
 #### Actividad 8: Feedback
 ##### 1. Continuar: ¿Qué actividad, explicación o ejemplo de esta unidad te ayudó más a entender el poder de las máquinas de estados? ¿Qué elemento consideras que es indispensable y debería mantener?
 La actividad que más me ayudó a entender las cosas fue en la que cambian las caritas.
 ##### 2. Dejar de hacer: ¿Hubo algún paso o actividad que te pareció confuso, innecesariamente complicado o que aportó poco a tu aprendizaje? ¿Qué cambiarías o eliminarías?
 Me pareció complicado la creación de un objeto, creo que sería mejor explicar primero lo de crear un método que se llame siempre con el while y luego lo de la clase, no sé si me hice entender.
 ##### 3. Empezar a hacer: ¿Qué te habría ayudado a entender mejor?
 No sé si el explicar con un ejercicio un poco más sencillo lo de la cración de objetos.
 ##### 4. Ritmo y dificultad: En una escala del 1 (muy fácil) al 5 (muy difícil), ¿Cómo calificarías la dificultad de pasar del análisis de un programa (Actividad 03) al diseño desde cero de uno complejo (Actividad 04 y 05)? ¿Por qué?
 Está bien, sería un 3.

   
