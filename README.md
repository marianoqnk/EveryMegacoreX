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
En la programación los fusibles que podemos cambiar y que no hace el cálculo de los valor el platformio son:


 * board_hardware.bod= 1.8v cambia el valor del BOD los posibles valores son: 
    |   BOD|
   |------|
   |   4.3 V|
   |   4.0 V |
   | 3.7 V  |
   |  3.3 V |
   | 2.9 V  |
   | 2.6 V (default option)  |
   |   2.1 V |
   | 1.8 V  |
   |Disabled|
 * board_build.f_cpu = 16000000L cambia la frecuencia del reloj, los valores son: 20 MHz	Internal oscillator, 16 MHz	Internal oscillator	Default option,10 MHz	Internal oscillator	Derived from 20 MHz osc.,8 MHz	Internal oscillator	Derived from 16 MHz osc., 5 MHz	ternal oscillator	Derived from 20 MHz osc., 4 MHz	Internal oscillator	Derived from 16 MHz osc., 2 MHz	Internal oscillator	Derived from 16 MHz osc.,1 MHz	Internal oscillator	Derived from 16 MHz osc.,20 MHz	External clock	,16 MHz	External clock	,12 MHz	External lock	,8 MHz	External clock	,1 MHz	External clock
    |   F. CLOCK|
   |------|
   |20 MHz	Internal oscillator  |
   | 16 MHz	Internal oscillator	Default option |
   | 10 MHz	Internal oscillator	Derived from 20 MHz osc. |
   | 8 MHz	Internal oscillator	Derived from 16 MHz osc. |
   | 5 MHz	ternal oscillator	Derived from 20 MHz osc. |
   |  4 MHz	Internal oscillator	Derived from 16 MHz osc. |
   | 2 MHz	Internal oscillator	Derived from 16 MHz osc. |
   | 1 MHz	Internal oscillator	Derived from 16 MHz osc. |
   | 20 MHz	External clock |
   |16 MHz	External clock  |
   | 12 MHz	External lock |
   | 8 MHz	External clock	 |
   | 1 MHz	External clock|
   
 * board_hardware.eesave=yes Con este fusible indicamos si se borra la EEPROM o se conserva cuando grabamos el micro
 * board_hardware.rstpin=Reset/gpio indicamos si el pin que utiliza el reset es de reset o lo queremos utilizar como I/O pin. En el arduino Every la grabación se realiza por UPDI por lo que el pin de reset no se utiliza en la grabación y para lo único que sirve es para el reset manual.
 * El resto de los fusibles si queremos programarlos hay que hacerlo directamente, no he encontrado ninguna calculadora para hacerlo. Las opciones son:
   
|   FUSES|
   |------|
|board_fuses.wdtcfg = 0x00|
|board_fuses.bodcfg = 0x00|
|board_fuses.osccfg = 0x01|
|board_fuses.tcd0cfg = 0x00|
|board_fuses.syscfg0 = 0xC9|
|board_fuses.syscfg1 = 0x06|
|board_fuses.append = 0x00|
|board_fuses.bootend = 0x00|
;board-fuses.lockbit = 0xc5
