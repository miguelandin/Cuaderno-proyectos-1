Lector de código morse en dos arduinos.
```c
/* 
Autor: -------------------
Descripción: Programa esclavo (RX) para comunicación con Arduino
Última modificación :  Enero 2025
*/

//Definiciones
#include <LiquidCrystal.h>
#define pin_RS 14
#define pin_E   15
#define pin_DB4 16
#define pin_DB5 17
#define pin_DB6 18
#define pin_DB7 19


//Variables

String simbolo="";
String letra="";

// Se crea el objeto pantalla con cuatro líneas de datos
LiquidCrystal pantalla(14,15,16,17,18,19);


void setup() {
	Serial.begin(9600);
  	pantalla.begin(16,2);
}

void loop() {

  // ........................ código
 if (Serial.available() > 0) {
        char recibido = Serial.read(); // Leer el carácter recibido

        switch (recibido) {
            case 'p':
                simbolo += '.';
                pantalla.print('.');
                break;

            case 'r':
                simbolo += '-';
                pantalla.print('-');
                break;

            case 'c':
                letra += conversion_letra(simbolo);
          		pantalla.clear();
          		pantalla.setCursor(0,1);
                pantalla.print(letra);
                simbolo = "";
                pantalla.setCursor(0,0);            
                break;

            case 'b':
                simbolo = quitarcaracter(simbolo);
                pantalla.clear();
          		pantalla.print(simbolo);
                pantalla.print(letra);
                break;

            case 'e':
                simbolo = "";
                letra = "";
                pantalla.clear();
                break;
        }
    }
}


//////////////////////////////Quitar el último caracter de un String

String quitarcaracter(String simbolo){

 unsigned int numero=0;// número de caracteres del string
 numero = simbolo.length();
 
  if (numero>0){ 
  numero=numero-1; // Se empieza a contar por el 0
  simbolo.remove(numero,1);   // Quita un caracter desde numero 
  }
  else{
  simbolo=""; // el string está vacío
  }
  return simbolo;
}



//////////////////////////////Conversor de símbolo en código a letra o número

char conversion_letra(String simbolo) {

  char letra='?'; // si no es un código correcto se mostrará este símbolo de interrogación


  if (simbolo == ".-") {
    letra = 'A';
  }

  if (simbolo == "-...") {
    letra = 'B';
  }

  if (simbolo == "-.-.") {
    letra = 'C';
  }

  if (simbolo == "-..") {
    letra = 'D';
  }

  if (simbolo == ".") {
    letra = 'E';
  }

  if (simbolo == "..-.") {
    letra = 'F';
  }

  if (simbolo == "--.") {
    letra = 'G';
  }

  if (simbolo == "....") {
    letra = 'H';
  }

  if (simbolo == "..") {
    letra = 'I';
  }

  if (simbolo == ".---") {
    letra = 'J';
  }

  if (simbolo == "-.-") {
    letra = 'K';
  }

  if (simbolo == ".-..") {
    letra = 'L';
  }

  if (simbolo == "--") {
    letra = 'M';
  }

  if (simbolo == "-.") {
    letra = 'N';
  }

  if (simbolo == "---") {
    letra = 'O';
  }

  if (simbolo == ".--.") {
    letra = 'P';
  }
  if (simbolo == "--.-") {
    letra = 'Q';
  }

  if (simbolo == ".-.") {
    letra = 'R';
  }

  if (simbolo == "...") {
    letra = 'S';
  }

  if (simbolo == "-") {
    letra = 'T';
  }

  if (simbolo == "..-") {
    letra = 'U';
  }

  if (simbolo == "...-") {
    letra = 'V';
  }

  if (simbolo == ".--") {
    letra = 'W';
  }

  if (simbolo == "-..-") {
    letra = 'X';
  }

  if (simbolo == "-.--") {
    letra = 'Y';
  }

  if (simbolo == "--..") {
    letra = 'Z';
  }

  if (simbolo == ".----") {
    letra = '1';
  }

  if (simbolo == "--...") {
    letra = '2';
  }

  if (simbolo == "...--") {
    letra = '3';
  }

  if (simbolo == "....-") {
    letra = '4';
  }

  if (simbolo == ".....") {
    letra = '5';
  }

  if (simbolo == "-....") {
    letra = '6';
  }

  if (simbolo == "--..") {
    letra = '7';
  }

  if (simbolo == "---..") {
    letra = '8';
  }

  if (simbolo == "----.") {
    letra = '9';
  }
if (simbolo == "-----") {
    letra = '0';
  }

  return letra;
}

```