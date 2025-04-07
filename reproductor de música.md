
Proyecto del primer cuatrimestre de proyectos 1.
[proyecto](https://www.tinkercad.com/things/faplTXGmeK8-reproductor-musica)

![[reproductor música.png]]

```c++
#include <LiquidCrystal.h>
#include <Servo.h>
#define entrada A3
#define buzz A2
#define boton 2
#define rojo 9
#define verde 8
#define motor 13

LiquidCrystal pantalla(12,11,4,5,6,7); //definimos el objeto LCD
Servo myServo; //definimos el objeto servo

int menu;
int entrada0;
bool play = false;
String status = "play";

void setup()
{
  //definimos los pines
  pinMode(entrada, INPUT); //potenciómetro para el menú
  pinMode(buzz, OUTPUT); //salida de audio
  pinMode(boton, INPUT); //boton de play
  pinMode(rojo, OUTPUT); //led rojo
  pinMode(verde, OUTPUT); //led azul
  myServo.attach(motor); //motor servo
  
  Serial.begin(9600); //velocidad de lectura de consola
  
  pantalla.begin(16,2); //16 cols, 2 filas en el LCD
  
  Update();//visualizar menu, leds, servo.
}

void loop()
{
  PotenStatus();
  
  PlayStatus();
}
  
  
  void UpdateMenu()//actualiza el estado del menu
{
    switch (menu){ //usa el valor de menu para el switch
    case 0:
      pantalla.clear();
      pantalla.print("Cancion 1");
      pantalla.setCursor(0,1);
      pantalla.print(status);
      pantalla.setCursor(0,0);
      
      if(play){ //comprueba que se pueda reproducir
        delay(200); //delay para que no de problemas
        cancion0();
      }
    break;
    case 1:
      pantalla.clear();
      pantalla.print("Cancion 2");
      pantalla.setCursor(0,1);
      pantalla.print(status);
      pantalla.setCursor(0,0);
      
      if(play){ //comprueba que se pueda reproducir
        delay(200); //delay para que no de problemas
        cancion1();
      }
    break;
    case 2:
      pantalla.clear();
      pantalla.print("Cancion 3");
      pantalla.setCursor(0,1);
      pantalla.print(status);
      pantalla.setCursor(0,0);
      
      if(play){ //comprueba que se pueda reproducir
        delay(200); //delay para que no de problemas
        cancion2();
      }
    break;
    default:
      pantalla.clear();
      pantalla.print("Error");
    }
}

void PotenStatus()
{
    entrada0 = analogRead(entrada); //lee el valor del potenciómetro
  entrada0 = map(entrada0, 0, 900, 0, 2); //rango de 0 a 2
  
  if(menu != entrada0)//comprueba que se haga un cambio
  {
    menu = entrada0; //se actualiza el nuevo cambio
    play=false;
    status="play";
    Update();
  }
}

void PlayStatus()//comprueba si se presiona el boton de play
{
  if(digitalRead(boton) == HIGH && play == false)
  {
    play = true;//cambia el estado
    status="reproduciendo...";//cambia el mensage de estado
    Update();
    delay(500);//delay para evitar problemas
  }
  if(digitalRead(boton) == HIGH && play == true)
  {
    play = false;//cambia el estado
    status="play";//cambia el mensaje de estado
    Update();
    delay(500);//poner delay para que no explote
  }
}

void UpdateLed()//actualiza el estado de los leds
{
  if(play)
  {
    digitalWrite(rojo, 0);
    digitalWrite(verde, 1);
  }
  else
  {
    digitalWrite(verde,0);
    digitalWrite(rojo, 1);
  }
}

void UpdateServo()//actualiza el estado del motor servo
{
  if(play)
  {
    myServo.write(90);//angulo de 90º
  }
  else if(!play)
  {
    myServo.write(0);//angulo de 0º
  }
  delay(15);
}

void Update()//actualiza todo
{
  UpdateServo();
  UpdateLed();
  UpdateMenu();
}

void cancion0(){//reproduce cancion 1
  while(play){
    tone(buzz,1);
    PotenStatus();
    PlayStatus();
  }
}

void cancion1(){//reproduce cancion 2
  while(play){
    tone(buzz,3);
    PotenStatus();
    PlayStatus();
  }
}

void cancion2(){//reproduce cancion 3
  while(play){
    tone(buzz,5);
    PotenStatus();
    PlayStatus();
  }
}
```