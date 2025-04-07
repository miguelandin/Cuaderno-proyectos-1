```c++
bool leeboton(byte entrada, int retardo) {
  static bool ent_anterior = 0;
  static unsigned long tiempo_ultima = millis();
  bool ent_actual = 0;
  bool salida = 0;
  unsigned long tiempo = millis();
  
  if (tiempo > tiempo_ultima + retardo) {
    tiempo_ultima = millis();
    ent_actual = digitalRead(entrada);
    
    if (ent_actual == 1 && ent_anterior == 0) {
      salida = 1;
      ent_anterior = 1;
    }
    
    if (ent_actual == 0) {
      ent_anterior = 0;
    }
  }
  
  return salida;
}

```