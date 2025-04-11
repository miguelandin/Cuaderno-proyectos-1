```C++
#define ejeX A0
#define ejeY A1
#define pulsador 11
#define enable 7
#define pin_A1 6
#define pin_A2 5

void setup()
{
pinMode(pulsador, INPUT_PULLUP);
pinMode(ejeX, INPUT);
pinMode(ejeY, INPUT);
pinMode(enable, OUTPUT);
pinMode(pin_A1, OUTPUT);
pinMode(pin_A2, OUTPUT);
Serial.begin(9600);
}

  

void loop() {
byte velocidad = 0;
int X = analogRead(ejeX);
int Y = analogRead(ejeY);
bool presion = digitalRead(pulsador);
if (X < 529) {
digitalWrite(pin_A1, HIGH);
digitalWrite(pin_A2, LOW);
} else if (X > 569) {
digitalWrite(pin_A1, LOW);
digitalWrite(pin_A2, HIGH);
} else {
digitalWrite(pin_A1, LOW);
digitalWrite(pin_A2, LOW);
}

if (Y < 516) {
velocidad = map(Y, 516, 0, 0, 255);
} else if (Y > 556) {
velocidad = map(Y, 556, 1023, 0, 255);
} else {
velocidad = 0;
}
  
if (presion) {
analogWrite(enable, velocidad);
} else {
analogWrite(enable, 0);
}
}
```