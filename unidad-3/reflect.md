# Unidad 3
## Fase: Set-seek
### Actividad 1
Código semáforo:
```python
from microbit import *
import utime


class Semaforo():
    def __init__(self,fila,timeR,timeY,timeG):
        self.state = "waitR"
        self.startTime = utime.ticks_ms()
        self.fila = fila
        self.timeR = timeR
        self.timeY = timeY
        self.timeG = timeG
        display.set_pixel(0,self.fila,9)

    def update(self):

        if self.state == "waitR":
            if utime.ticks_diff(utime.ticks_ms(),self.startTime) >= self.timeR:
                display.set_pixel(0,self.fila,0)
                display.set_pixel(2,self.fila,9)
                self.startTime = utime.ticks_ms()
                self.state = "waitY"
                    
        elif self.state == "waitY":
            if utime.ticks_diff(utime.ticks_ms(),self.startTime) >= self.timeY:
                display.set_pixel(2,self.fila,0)
                display.set_pixel(4,self.fila,9)
                self.startTime = utime.ticks_ms()
                self.state = "waitG"

        elif self.state == "waitG":
            if utime.ticks_diff(utime.ticks_ms(),self.startTime) >= self.timeG:
                display.set_pixel(4,self.fila,0)
                display.set_pixel(0,self.fila,9)
                self.startTime = utime.ticks_ms()
                self.state = "waitR"

semaforo1 = Semaforo(0,5000,2000,3000)
semaforo2 = Semaforo(2,3000,1000,2000)
semaforo3 = Semaforo(4,4000,3000,2000)

while True:
    semaforo1.update()
    semaforo2.update()
    semaforo3.update()
```
### Actividad 2

## 🤔 Fase: Reflect
### Autoevaluación
#### Parte 1:
1. Describe con tus palabras, ¿qué es una maquina de estados y cúales son sus cuatro componentes fundamentales?
   
   Una maquina de estados es una forma de modelar el programa y sus componentes principales son los estados, los eventos, las acciones y las transiciones.
2. ¿Por qué la técnica de máquinas de estado es tan útil para gestionar la concurrencia?¿Qué problema soluciona en comparación con usar funciones como sleep()?
   
   Es útil ya que no bloquea el programa, como lo haría si utilizamos el sleep(); lamaquina de estados permite hacer otras cosas mientras esta ocurriendo algo mas.
3. Imagina que tienes que añadir una nueva funcionalidad a la bomba: si se recibe un evento especial, mientras la cuenta regresiva está activa, el tiempo se reduce a la mitad. ¿Cómo modificarías tu diagrama de máquina de estados para incluir este nuevo evento y acción?
   
   No sé
4. Explica qué es un “vector de prueba” y por qué es una herramienta crucial para verificar que una máquina de estados funciona como se espera.
   
   Un vector de prueba es una manera de testear que el programa funcione tal y como nosotros esperamos, ya que verificamos que realice las acciones que tiene que hacer, que cambie de estado tras una accion o evento, etc. Es muy útil porque nos muestra que el programa si esta funcionando como seplanteó.

   


