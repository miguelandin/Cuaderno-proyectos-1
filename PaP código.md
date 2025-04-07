```C
#define A 4
#define B 5
#define C 6
#define D 7

const byte Tabla_pasos[4] = {B0001, B0010, B0100, B1000};

void setup() {
Serial.begin(9600);
pinMode(A, OUTPUT);
pinMode(B, OUTPUT);
pinMode(C, OUTPUT);
pinMode(D, OUTPUT);
}

void loop() {
for(int paso = 0; paso < 4; paso++) {
digitalWrite(A, bitRead(Tabla_pasos[paso], 0));
digitalWrite(B, bitRead(Tabla_pasos[paso], 1));
digitalWrite(C, bitRead(Tabla_pasos[paso], 2));
digitalWrite(D, bitRead(Tabla_pasos[paso], 3));
delay(10);
}
}
```