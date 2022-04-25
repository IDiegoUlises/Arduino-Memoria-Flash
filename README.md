# Arduino Memoria Flash
Como guardar datos en la memoria flash con la libreria, recordar que la memoria flash se guarda los datos aunque el arduino pierda la fuente de alimentacion

#include <avr/pgmspace.h>
const char string_0[] PROGMEM = "String 0"; // "String 0" etc are strings to store - change to suit.
const char string_1[] PROGMEM = "String 1";
const char string_2[] PROGMEM = "String 2";
const char string_3[] PROGMEM = "String 3";
const char string_4[] PROGMEM = "String 4";
const char string_5[] PROGMEM = "String 5";
