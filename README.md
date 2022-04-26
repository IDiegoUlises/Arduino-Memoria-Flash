# Arduino Memoria Flash
La memoria flash es donde el sketch del arduino en binario es almacenado, esta dividida en dos zonas una para el bootloader y otra para almacenar el sketch por esta razon solo es posible almacenar los datos al mismo tiempo que se compila el sketch.

```c++
#include <avr/pgmspace.h>

//Se crea arrays
const char cadena_0[] PROGMEM = "Cadena 0"; //Aqui guarda el valor de la variable
const char cadena_1[] PROGMEM = "Cadena 1";
const char cadena_2[] PROGMEM = "Cadena 2";


//Se declara la variable como un modificador de variable y guarda los array en la memoria flash
const char* const tabla[] PROGMEM = {cadena_0, cadena_1, cadena_2,};

//Este array se almacena en la memoria Sram(Ram Estatica) del Arduino
char arreglo[10]; //El array debe ser lo suficientemente grande para almacenar la cadena

void setup()
{
  Serial.begin(9600);
}

void loop()
{
  for (int i = 0; i < 3; i++) //Recorre el array mostrando cada arreglo
  {
    strcpy_P(arreglo,(char*)pgm_read_word(&(tabla[i]))); //Realiza un copia de la variable almacenada en la memoria flash en la variable arreglo
    Serial.println(arreglo);
    delay(500);
  }
}
```
# ¿Cuando Guardar Datos en la Memoria Flash?
Cuando se guarde muchos datos y que la memoria Sram(Ram estatica) del Arduino no tenga capacidad suficiente para almacenar todos los datos.

* **La memoria flash es mucho mas rapida que la memoria EEPPROM**
* **La memoria flash no tiene limite de escritura es decir que puede ser modificada infinitamente**
* **La memoria flash no tiene limite de borrado**

# Guardar Datos en la Memoria Flash Cuando se Imprime Texto 
<p align="center">
  <img  src="https://github.com/IDiegoUlises/Arduino-Memoria-Flash/blob/main/Images/Hola-Mundo.jpg">
</p>

* ## Este es un hola mundo normal ocupa 198 bytes

<p align="center">
  <img  src="https://github.com/IDiegoUlises/Arduino-Memoria-Flash/blob/main/Images/Hola-Mundo-Con-F.jpg">
</p>

* ## Este es un hola mundo normal ocupa 188 bytes

