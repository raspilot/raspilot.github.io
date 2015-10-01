---
layout: page-fullwidth
title: "Developer"
subheadline: "How to use RasPilot"
teaser: "The documentation is a work in progress..."
permalink: "/developer/"
header: no
---

##Where is the latest code
Although ardupilot official code contains the RasPilot part, the latest code will be commited firstly to <strong>raspilot-master</strong> branch on raspilot github page.

1. Ardupilot (runs on Raspberry Pi):  [https://github.com/raspilot/ardupilot/tree/raspilot-master](https://github.com/raspilot/ardupilot/tree/raspilot-master)
2. Firmware (runs on STM32):  [https://github.com/raspilot/Firmware](https://github.com/raspilot/Firmware)
3. Bootloader (runs on STM32):  [https://github.com/raspilot/Bootloader](https://github.com/raspilot/Bootloader)
4. Hardware schematic & layout:  [https://github.com/raspilot/Hardware](https://github.com/raspilot/Hardware)

##Step-by-step guide for building from soure
Limited by the CPU performance, building souce code on Raspberry Pi could be very slow. So it's strongly recommended to cross-compile the code on PC with Linux (e.g. Ubuntu 14.04 LTS).

###Download the cross-compile tool
Raspberry Pi Foundation provides an ARM crossc-compile tool [here](https://github.com/raspberrypi/tools), works both on Raspberry 1 & 2.

First download the tool to PC.

~~~
sudo git clone --depth 1 https://github.com/raspberrypi/tools.git
~~~

Then copy the crossc-compile tool package to /opt

~~~
sudo cp tools /opt
~~~

###Add path to the environment config
For 32-bit distro Linux:

~~~
export PATH=/opt/tools/arm-bcm2708/gcc-linaro-arm-linux-gnueabihf-raspbian/bin:$PATH
~~~

For 64-bit distro Linux:

~~~
export PATH=/opt/tools/arm-bcm2708/gcc-linaro-arm-linux-gnueabihf-raspbian-x64/bin:$PATH
~~~

To apply the config permanently, please edit ~/.bashrc file and reboot.

###Download source code
Download ardupilot source code from RasPilot Github repository.

~~~
git clone https://github.com/raspilot/ardupilot
~~~

Checkout the raspilot-master branch.

~~~
cd ardupilot
git checkout raspilot-master
~~~

###Build APM
Build for quad-copter:

~~~
cd ArduCopter
make raspilot
~~~

Build for hexa-copter:

~~~
cd ArduCopter
make raspilot-hexa
~~~

And so on, build for other frame type, just replace the word behind "-" to the following:

~~~
quad tri hexa y6 octa octa-quad heli single obc nologging
~~~

Build for fixed-wing plane:

~~~
cd ArduPlane
make raspilot
~~~

Build for APMrover2:

~~~
cd APMrover2
make raspilot
~~~

###Upload the binary to Raspberry Pi
For example, after building of ArduCopter complete, the binary will located in /tmp/ArduCopter.build

Use scp command to transfer the binary to Raspberry Pi. (assume the IP address of Raspberry Pi is 192.168.1.100)

~~~
scp /tmp/ArduCopter.build/ArduCopter.elf pi@192.168.1.100:/home/pi
~~~
