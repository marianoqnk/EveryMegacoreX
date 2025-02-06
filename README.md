# EveryMegacoreX
Como utilizar el Arduino nano Every con el MegacoreX en platformio.
Arduino Nano Every es una de las placas de estandar de Arduino. La diferencia principal es que lleva unmicrocontrolador Atmel Atmega 4809.
Información: 
  * [Información sobre la placa](https://store.arduino.cc/en-es/products/arduino-nano-every)
  * [DataSheet del ATmega4809](https://ww1.microchip.com/downloads/en/DeviceDoc/ATmega4808-4809-Data-Sheet-DS40002173A.pdf)
  * [Página que describe todos los recursos del Every](https://wolles-elektronikkiste.de/en/arduino-nano-every-a-deep-dive) 
Ahora lo que queremos es poder utyilizar el megacorex con esta placa. La razón principal de querer utilizar este en lugar del original es que en este tenemos nuevas opciones que no permiten tener un mayor control sobre la placa y además añade nuevas funciones que lo hacen muy interesante.
  * [MegaCoreX](https://github.com/MCUdude/MegaCoreX)
  * [Nuevas funciones del Megacorex](https://github.com/MCUdude/MegaCoreX/blob/master/Extended-API.md)

Debemos tener en cuenta que los pinout del Every con el megacore normal y con el meracorex son ligeramente distintos:

Ahora tenemos que ligarlo todo y para ello hemos creado el fichero platformio.ini que es el que nos configura Platformio para que todo funcione.
