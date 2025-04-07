El sensor ultrasonido utiliza las propiedades de propagación del sonido para medir distancias.

# Funcionamiento
+ El sensor envía una onda ultra-sónica a través del disipador.
+ Esta rebota contra el objeto y el receptor detecta la onda.
+ Sabiendo cuánto ha tardado en llegar dicha onda podemos saber la distancia.

$$S = v*t$$
Donde S es espacio, v velocidad y t tiempo.
El sonido en el aire viaja a 343 m/s.
# Sensor
+ Después de recibir la señal adecuada, el pin trigger, el dispositivo emite 8 pulsos ultrasonido de frecuencia 40kHz.
+ El pino **ECHO** cambia de nivel bajo a nivel alto al finalizar a transmisión de la señal de ultrasonidos y cambia a de nuevo a nivel bajo cuando la señal echo es recibida.
+ Por lo tanto, la duración del pulso indica el tiempo desde que la señal fue emitida hasta que fue recibida.

![[Pasted image 20250221094125.png]]

# Funciones
```c++
delayMicroseconds(x); // Es como un delay normal pero en microsegundos en vez de milisegundos

pulseIn(pin, LOW/HIGH); // Lee la duración de un pulso entre valores altos o bajos y devuelve el valor en microsegundos. Devuelve una longitud long unsigned de 32 bits

double CalcDist(int trigger, int echo) // función calcular distancia
{
  	static double long tiempo;
	static double espacio;
	static const int VelSonido = 343;
  
  	digitalWrite(trigger, 1); // activa ultrasonido
  	delayMicroseconds(10); // deja la señal activa 10 microsegundos
  	digitalWrite(trigger, 0); // baja el trigger
  	tiempo = pulseIn(echo, 1)/2; // lee el tiempo de llegada
  	tiempo = tiempo / 1000000; // convierte los microsegundos a segundos
  	espacio = tiempo * VelSonido; // 343 m/s velocidad del sonido en aire

  	return espacio;// devuelve distancia en metros
}
```

# [Ejemplo](https://www.tinkercad.com/things/go6aPTBlUr0-ultrasonido)