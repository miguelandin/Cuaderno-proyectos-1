```c
Serial.begin(x); //velocidad de lectura del puerto serie
val = Serial.read(); //lee el puerto serie
Serial.print(val); //envía los dígitos de val
Serial.println(val); //envía los dígitos de val con un salto de línea
Serial.write(val); //envía el byte val
val = Serial.available(); //dara true si hay algo por leer en el buffer
```