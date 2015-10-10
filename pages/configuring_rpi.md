---
layout: page-fullwidth
title: "Configuring RPi"
subheadline: "How to use RasPilot"
teaser: "The documentation is a work in progress..."
permalink: "/configuring_rpi/"
header: no
---

For detailed instructions of using Raspberry Pi, please visit the official documentation of Raspberry Pi Foundation.<br>
[https://www.raspberrypi.org/documentation/](https://www.raspberrypi.org/documentation/)

##Writing an (Linux) image to the SD card
Default Raspbian kernel is compiled with PREEMPT option which has a serious latency on interrupt calling. To ensure the ardupilot task to be executed within low latency time, we patched the Raspbian kernel with [Real-Time patch](https://rt.wiki.kernel.org). Please download the latest Linux image in the Download Page [here](http://raspilot.io/downloads/).

Then follow the installing-image instruction on Raspberry Pi Foundation page.

* [Linux](https://www.raspberrypi.org/documentation/installation/installing-images/linux.md)
* [Mac OS](https://www.raspberrypi.org/documentation/installation/installing-images/mac.md)
* [Windows](https://www.raspberrypi.org/documentation/installation/installing-images/windows.md)

##Access from Ethernet cable
Raspberry Pi B+ / 2B has a Ethernet port. Connect it to your router with a Ethernet cable. The Raspberry Pi can get IP address automatically. And you could look up the device "raspilot" in the router setting page.

##Access from USB WiFi dongle
To setup the WiFi router you want to connect, edit <strong>/etc/wpa_supplicant/wpa_supplicant.conf</strong> on the SD card in Raspberry Pi console, or in a Linux environment on PC. Add the following lines to the end of the file (replace "yourssid" & "yourpasskey" to fit your WiFi environment).

~~~
network={
  ssid="yourssid"  
  psk="yourpasskey"
  key_mgmt=WPA-PSK
}
~~~

Please read the [INSTRUCTIONS](https://www.raspberrypi.org/documentation/configuration/wireless/README.md) on Raspberry Pi Foundation pages for more information.

##Remote access to Raspberry Pi
The serial port on Raspberry Pi 40pin connector is used for getting GPS data, so you can not access console from that.<br>
It is recommended to access Raspberry Pi via [SSH](https://www.raspberrypi.org/documentation/remote-access/ssh/README.md).

Please read the [INSTRUCTIONS](https://www.raspberrypi.org/documentation/remote-access/) on Raspberry Pi Foundation pages for more information.
