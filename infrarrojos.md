Para el uso de infrarrojos necesitamos un emisor y un receptor.  En nuestro kit de [[arduino]] sería el **mando a distancia infrarrojos** y el **receptor de infrarrojos**.

# luz infrarroja
La luz infrarroja está por debajo del espectro visible por el ojo humano, por lo que estas señales no son detectables a simple vista.

# mando
El mando tiene un led que emite señales en el espectro infrarrojo, consistente en pulsas con distinta codificación.

# detector
EL detector consta de un fotodiodo capaz de traducir las señales infrarrojas en señales eléctricas dando niveles de 0V(0) a 5V(1).
El emisor y el detector usan un [[protocolo comunicación IR]].

# código
+ Primero instalamos la librería de IR
```c++
#include <IRremote.h>
```
+ Inicializamos el infrarrojo
```c++
IrReceiver.begin (pin_recep);
```
+ Operamos
```c++
IrReceiver.decode(); // devulve 1 si hay algun dato decodificado

variable = IrReceiver.decodedIRData.decodedRawData // lectura de la última trama, devuelve un long

variable = IrReceiver.decodedIRData.command // lectura del comando recibido

IrReceiver.printIRResultShort(&Serial); // Saca información por el puerto serie sobre el protocolo y datos usados

IrReceiver.resume(); // reseteo del receptor para permitir un nueva lectura
```

# [Ejemplo](https://www.tinkercad.com/things/gIVVhpJCDLf-infrarrojo)