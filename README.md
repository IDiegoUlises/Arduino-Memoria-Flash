# Arduino Memoria Flash
La memoria flash es donde el sketch del arduino en binario es almacenado, esta dividida en dos zonas una para el bootloader y otra para almacenar el sketch.

```c++
#include <avr/pgmspace.h>

//Se crea arrays
const char cadena_0[] PROGMEM = "Cadena 0"; //Aqui guarda el valor de la variable
const char cadena_1[] PROGMEM = "Cadena 1";
const char cadena_2[] PROGMEM = "Cadena 2";


//Se declara la variable como un modificador de variable y guarda los array en la memoria flash
const char* const tabla[] PROGMEM = {cadena_0, cadena_1, cadena_2,};

//Este array se almacena en la memoria Sram(Ram Estatica) del Arduino
char arreglo[30]; //El array debe ser lo suficientemente grande para almacenar la cadena

void setup()
{
  Serial.begin(9600);
}

void loop()
{
  for (int i = 0; i < 3; i++) //Recorre el array mostrando cada arreglo
  {
    strcpy_P(arreglo,(char*)pgm_read_word(&(tabla[i]))); // Realiza un copia de la variable almacenada en la memoria flash en la variable arreglo
    Serial.println(arreglo);
    delay(500);
  }
}
```
