# Pulu-hardware

All information of the hardware of the pulu project from Pojectwerk Vives is found here.  

## Hardware group

* Dylan Missuwe  
* Timon Claerhout  
* Seppe Dewitte  
* Tybris Vandenbroucke  
* Aaron Degroote  

## Intro

All students of Elektronica-ICT had the assignment to work together on a project for the course Projectwerk of Vives Brugge.  

Belgium is the most affected by extreme drought in Europe so we build a project on that subject.  
We had to measure water contents indirectly by using capacitance sensors and send that data to an application so we can see those values. We have to do all this with using as little energy as possible.  

To manage this huge project we split up in 4 groups:  

* hardware  
* software  
* devops  
* firmware  

## PCB

| Front | Back |
|---|---|
| ![Front](./img/PCB_front.PNG) | ![Back](./img/PCB_back.PNG) |

### Shematic

![Shematic PCB](./img/PCB_shematic.PNG)

## Features

### Lora chip

In order to transmit the data without using mush power we use LoRaWAN.  
We are using the FRM95W lora chip for that:  

![Lora chip](./img/RFM95W.PNG)

We picked this chip because its compact and doesn't use much power.  
It has an RX current of 10.3 mA, 200 nA register retention.  
For reading and writing the sensors we're using I2C communication.  

### Crypto chip

We are using the ATECC508A crypto chip.  

![Crypto chip](./img/ATEC.PNG)

This is for encrypting our data so its much more secure to transmit and recieve.  
He uses an SHA-256 Hash Algorithm with HMAC Option that provides an 256-bit key length.  

The chip can store up to 16 keys.  

It also doens't need much power, in sleep current: <150 nA.  

### Moisture sensor

To measure the water contents in the ground we use moisture sensors.  
We provided copper tapes every 25 cm by the sensor so we can see the capacitance on 4 different depths:  

We are using the FDC1004 moisture sensor:  

![Moisture sensor](./img/FDC1004.PNG)

Because this is a 4 channel capacitance to digital converter (so we can measure on 4 different depths).  
Each channel has a full-scale range of ±15pF and can handle a sensor offset capacitance of up to 100pF.  
It also doesn't need much power:

* Active mode: 750 µA
* Standby mode: 29 µA

We have also written a library of the moisture sensor which can be found here:  
[Moisture sensor driver](https://github.com/vives-projectwerk-2021/pulu-moisture-sensor.git)

### Temperature sensor

To measure the temperature we are using the TCN75AVOA713 sensor.  

![Temperature sensor](./img/TNC75.PNG)

The sensor can measure temperatures from -40 °C to 125 °C with an 1 °C accuracy.  
It also consumes not much power:

* Operating Current: 200 µA (typical)
* Shutdown Current: 2 µA (maximum)

We have also written a library of the temperature sensor which can be found here:
[Temperature sensor driver](https://github.com/vives-projectwerk-2021/pulu-temperature-sensor.git)

### Light sensor

To measure the light we are using the TCN75AVOA713 lux sensor.  

![Light sensor](./img/LTR329.PNG)

The sensor can measure light from 0.01 lux to 64k lux with an 16-bit effective resolution.  
It also consumes not much power:

* Operating Current: 220 µA
* Standby Current: 5 µA

We have also written a library of the light sensor which can be found here:
[Light sensor driver](https://github.com/vives-projectwerk-2021/lightSensorDriver.git)

### Other

The PCB has other functions such as:

* USB-C connection with ESD protection
* AA Battery voltage monitoring
* EEPROM (24LC64-I_SN) for storing data
* LED for testing out communication PCB

### Case for PCB

To make sure our PCB stays waterproof we are using a PVC tube with ...
