Es un conjunto de reglas y estándares que permiten la comunicación de datos a través de señales de luz [[infrarrojos]].

# Funcionamiento
+ La onda portadora tiene un periodo de **26 microsegundos**.
+ Cada pulso es de 560 microsegundos, algo más de **21 ciclos** de la señal portadora.
+ Para codificar los ceros y unos se utiliza la diferencia de tiempo entre un puso y el siguiente. 
+ Si llega 2.25ms después se considera un 1.
+ Si llega 1.12ms después se considera un 0.
+ Para establecer la conexión entre emisor y receptor se hace primero una **trama de 67.8ms** de los cuales los primeros 9ms son de sincronización, luego 4.5ms no se emite nada y después se envían 8 bits con la dirección y 8 bits de comando.
+ Cada bloque de bits se repite para prevenir errores.