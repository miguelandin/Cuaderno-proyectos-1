A la hora de cablearlo tener en cuenta:
+ El cable amarillo va a un pin.
+ El cable amarillo va a voltaje.
+ El cable marrón va a tierra.
+ **Importante no conectarlo a el puerto 13**.
# programación
```c++
#include <Servo.h>

Servo nombre; //definimos el objeto servo

void setup(){
nombre.attach(pin); //establecemos en que pin recibe la señal
}

void loop(){
nombre.write(0); //el motor gira a un ángulo de 0º
delay(15); //importante poner delay para que no de problemas

nombre.write(90); //el motor gira a un ángulo de 90º
delay(15);
```

# [Ejemplo](https://www.tinkercad.com/things/a9e0w3Ct8I9-servomotor)