Para usar un motor de precisión como este, se usará un [[controlador ULN2003]].

+ Al hacer pasar corriente por una bobina del estator, el campo magnético creado hace que las marcas dentadas del estator y del rotor se alineen.
-  <a href="https://commons.wikimedia.org/w/index.php?curid=10011776">Ejemplo</a>

# Características
- Este motor gira en incrementos discretos de forma precisa.
- La dirección de rotación del motor está determinado por el orden de la secuencia de pulsos recibidos.
- La velocidad de rotación depende de la frecuencia de los pulsos recibidos.
- **Tensión**: $[5,12] VDC$.
- Tiene **4 fases** que son el número de [[bobinas]].
- **Temperaturas de** $-45ºC : 125ºC$.
- Cada posición son $11,25º$ -> 32 posiciones son una vuelta.
- El retardo entre pulsos es de $10ms$.
- Tiene una alta resistencia, por eso usamos un [[controlador ULN2003]].

# funcionamiento
- En cada ciclo se manda una corriente a una de las bobinas.
- Cada ciclo el rotor se moverá un paso.
- Entre dos ciclos consecutivos debemos guardar $10 ms$.
- **2048** ciclos o pasos para hacer una vuelta completa.
- Usaremos la función [[bitRead()]]

| Ciclo | Bobina4  | Bobina3  | Bobina2  | Bobina1  |
| ----- | -------- | -------- | -------- | -------- |
| 1     | ==HIGH== | LOW      | LOW      | LOW      |
| 2     | LOW      | ==HIGH== | LOW      | LOW      |
| 3     | LOW      | LOW      | ==HIGH== | LOW      |
| 4     | LOW      | LOW      | LOW      | ==HIGH== |

- [[PaP código]]