
# BMP085 - Arduino I2C library
C++ library for BMP085 barometer for I2C communication with Arduino Wire library.  Main features:
- read raw data
- calculate scaled data
- registers setting
- waiting for readout without delay (the conversion time is 25.5ms at maximum)
- moving average filtering (for pressure and temperature)

The library is intended to work **without any user interference**, just open [project](https://github.com/MatthewPatyk/BMP085-Arduino-I2C-library/blob/master/BMP085_.atsln) and upload working [example](https://github.com/MatthewPatyk/BMP085-Arduino-I2C-library/blob/master/BMP085_/BMP085_.ino) and use it.

Library uses [I2C Interface](https://github.com/MatthewPatyk/I2C-Interface-for-Arduino-Wire-Library), [I2C Sensor Interface](https://github.com/MatthewPatyk/I2C-Sensor-Interface) to simplify and unify working with I2C devices. The library also uses [Status Class](https://github.com/MatthewPatyk/Status-Class) which is optional.
 
## Getting Started
The working example for this library is writen in [Atmel Studio 7](http://www.microchip.com/mplab/avr-support/atmel-studio-7) with [Visual Micro](https://www.visualmicro.com/) addon. But **it is possible to run it with Arduino IDE** by [adding files to project](https://www.arduino.cc/en/Guide/Environment#toc8) (probably there will be need to change the `#include` paths).

### Prerequisites
- Software: 
	- [Atmel Studio 7](http://www.microchip.com/mplab/avr-support/atmel-studio-7) (tested) or Visual Studio,
	- [Visual Micro](https://www.visualmicro.com/) addon for above AS7 or VS.
- Hardware: 
	- Arduino Due (tested) or Arduino Uno (any ATmega 328P) board,
	- BMP085 board or any IMU sensor with BMP085.

### Wiring

|BMP085 board|Due board|Uno board|
| :------------: | :------------: | :------------: |
|SCL|SCL (21)|SCL (A4)|
|SDA|SDA (20)|SDA (A5)|
|VCC 3.3V|3.3V|3.3V|
|VCC 5V|- *|5V|
|GND|GND|GND|

 *The Due MCU cannot be exposed to the voltage above 3.3V level!
 
## Example 
To see a real-life example open AS7 project file `BMP085_.atsln` and upload the (`BMP085_.ino`) to a micro-controller. You should see somethink like that on Serial Monitor (baud rate = 115200):
```
2	Serial initialized with baudrate = 115200
6	Found BMP085 searching device with ID = 0x77
10	Pressure	0	Altitude	44330.00	Temperature	0.00
20	Pressure	0	Altitude	44330.00	Temperature	25.80
...
1260	Pressure	99237	Altitude	175.30	    Temperature	25.80
1271	Pressure	99237	Altitude	175.30	    Temperature	25.80
...
```

#### Mode setting (number of samples to average):
To change above in `BMP085_.ino` file uncommend and choose appropriate in below:

```
// Set Mode or use defaults from BMP085::init()
//	Barometer.setMode(->your_setting<-);
```

## Author 
* 2018, **Mateusz Patyk**, <matpatyk@gmail.com> 
 
## License 
- MIT License
