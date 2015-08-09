---
layout: page-fullwidth
title: "Specification"
subheadline: "RasPilot Hardware Specification"
teaser: "RasPilot is a Raspberry Pi HAT, which makes it possible for RPi to run as an autopilot."
permalink: "/specification/"
header: no
---

##Hardware Specification (v1.1)

###Features

* Raspberry Pi 1 A+/B+ / Raspberry Pi 2 B
* STM32F103 failsafe co-processor
* ArduPilot flight stack
* Pixhawk interface compatible
* USB (RPi) / Servo Rail BEC / Power Module three power inputs

###Sensors

* ST Micro L3GD20H gyro
* ST Micro LSM303D accel / mag
* Invensense MPU 9250 accel / gyro / mag
* MEAS MS5611 barometer

###Interfaces

* 2x UART (serial ports)
* 1x CAN (need external transmitter)
* 8x PWM
* Spektrum DSM / DSM2 / DSM-X® Satellite Receiver compatible
* Futaba S.BUS® compatible input and output
* PPM sum Receiver
* RSSI (PWM or voltage) Input
* 1x I2C
* 3.3V & 6.6V A/D input
* Safety switch
* Buzzer Interface
* Onboard tri-color LED

##Schematics
* [RasPilot_v1.0 schematic](https://github.com/raspilot/Hardware/raw/RASPILOT_V1/RASPILOTv1_0.sch)
* [RasPilot_v1.1 schematic]

##Connectors (v1.1)

##Pinouts (compatible with pixhawk)
POWER
<table>
  <thead>
    <td>Pin</td>
    <td>Signal</td>
    <td>Volt</td>
  </thead>
  <tr>
    <td>1</td>
    <td>VCC</td>
    <td>+5V</td>
  </tr>
  <tr>
    <td>2</td>
    <td>VCC</td>
    <td>+5V</td>
  </tr>
  <tr>
    <td>3</td>
    <td>CURRENT</td>
    <td>+3.3V</td>
  </tr>
  <tr>
    <td>4</td>
    <td>VOLTAGE</td>
    <td>+3.3V</td>
  </tr>
  <tr>
    <td>5</td>
    <td>GND</td>
    <td>GND</td>
  </tr>
  <tr>
    <td>6</td>
    <td>GND</td>
    <td>GND</td>
  </tr>
</table>

TELEM port
<table>
  <thead>
    <td>Pin</td>
    <td>Signal</td>
    <td>Volt</td>
  </thead>
  <tr>
    <td>1</td>
    <td>VCC</td>
    <td>+5V</td>
  </tr>
  <tr>
    <td>2</td>
    <td>TX(OUT)</td>
    <td>+3.3V</td>
  </tr>
  <tr>
    <td>3</td>
    <td>RX(IN)</td>
    <td>+3.3V</td>
  </tr>
  <tr>
    <td>4</td>
    <td>NC</td>
    <td>NC</td>
  </tr>
  <tr>
    <td>5</td>
    <td>NC</td>
    <td>NC</td>
  </tr>
  <tr>
    <td>6</td>
    <td>GND</td>
    <td>GND</td>
  </tr>
</table>

GPS port
<table>
  <thead>
    <td>Pin</td>
    <td>Signal</td>
    <td>Volt</td>
  </thead>
  <tr>
    <td>1</td>
    <td>VCC</td>
    <td>+5V</td>
  </tr>
  <tr>
    <td>2</td>
    <td>TX (OUT)</td>
    <td>+3.3V</td>
  </tr>
  <tr>
    <td>3</td>
    <td>RX (IN)</td>
    <td>+3.3V</td>
  </tr>
  <tr>
    <td>4</td>
    <td>CAN TX</td>
    <td>+3.3V</td>
  </tr>
  <tr>
    <td>5</td>
    <td>CAN RX</td>
    <td>+3.3V</td>
  </tr>
  <tr>
    <td>6</td>
    <td>GND</td>
    <td>GND</td>
  </tr>
</table>

I2C
<table>
  <thead>
    <td>Pin</td>
    <td>Signal</td>
    <td>Volt</td>
  </thead>
  <tr>
    <td>1</td>
    <td>VCC</td>
    <td>+5V</td>
  </tr>
  <tr>
    <td>2</td>
    <td>SCL</td>
    <td>+3.3V (pullups)</td>
  </tr>
  <tr>
    <td>3</td>
    <td>SDA</td>
    <td>+3.3V (pullups)</td>
  </tr>
  <tr>
    <td>4</td>
    <td>GND</td>
    <td>GND</td>
  </tr>
</table>

ADC 3.3V
<table>
  <thead>
    <td>Pin</td>
    <td>Signal</td>
    <td>Volt</td>
  </thead>
  <tr>
    <td>1</td>
    <td>VCC</td>
    <td>+5V</td>
  </tr>
  <tr>
    <td>2</td>
    <td>ADC IN</td>
    <td>up to +3.3V</td>
  </tr>
  <tr>
    <td>3</td>
    <td>GND</td>
    <td>GND</td>
  </tr>
  <tr>
    <td>4</td>
    <td>ADC IN</td>
    <td>up to +3.3V</td>
  </tr>
  <tr>
    <td>5</td>
    <td>GND</td>
    <td>GND</td>
  </tr>
</table>

ADC 6.6V
<table>
  <thead>
    <td>Pin</td>
    <td>Signal</td>
    <td>Volt</td>
  </thead>
  <tr>
    <td>1</td>
    <td>VCC</td>
    <td>+5V</td>
  </tr>
  <tr>
    <td>2</td>
    <td>ADC IN</td>
    <td>up to +6.6V</td>
  </tr>
  <tr>
    <td>3</td>
    <td>GND</td>
    <td>GND</td>
  </tr>
</table>

SWITCH
<table>
  <thead>
    <td>Pin</td>
    <td>Signal</td>
    <td>Volt</td>
  </thead>
  <tr>
    <td>1</td>
    <td>VCC</td>
    <td>+3.3V</td>
  </tr>
  <tr>
    <td>2</td>
    <td>!IO_LED_SAFETY</td>
    <td>GND</td>
  </tr>
  <tr>
    <td>3</td>
    <td>SAFETY</td>
    <td>GND</td>
  </tr>
</table>
