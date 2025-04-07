```c++
#define entrada A3 //definimos el pin A3 (está creando como un acceso directo)
#define salida 12 //definimos el pin 12

void setup(){
	pinMode(entrada, INPUT); //se establece como un pin de entrada
	pinMode(salida, OUTPUT); //se establece como un pin de salida
}

void loop(){
	int entrada0 = analogRead(entrada); //Lee el imput de A3
	digitalWrite(salida, 1); //Manda corriente al pin 12
}
```
