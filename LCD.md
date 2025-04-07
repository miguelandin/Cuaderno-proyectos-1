Para usar un LCD hay que hacer lo siguiente:
```c
#include <LiquidCrystal.h>
LiquidCrystal pantalla(12,11,4,5,6,7)//definimos el objeto
pantalla.begin(16,2) //establecemos en número de filas y columnas
pantalla.print(val) //mostrar en el LCD lo que contenga el valor
pantalla.clear(); //limpia la pantalla
pantalla.setCursor(col,fil); //establece en que fila escribir
```

Ejemplos: [[practica morse]]

# Cableado
+ En la entrada `VO` es recomendable usar un potenciómetro de 10K omios para ajustar el contraste.

# [Ejemplo](https://www.tinkercad.com/things/kfCoTVE9xXg-lcd)