---
layout: page-fullwidth
title: "Loading Software"
subheadline: "How to use RasPilot"
teaser: "The documentation is a work in progress..."
permalink: "/loading_software/"
header: no
---
<div class="row">
<div class="medium-4 medium-push-8 columns" markdown="1">
<div class="panel radius" markdown="1">
**Table of Contents**
{: #toc }
*  TOC
{:toc}
</div>
</div><!-- /.medium-4.columns -->


<div class="medium-8 medium-pull-4 columns" markdown="1">

##Download & setup APM binary
Download APM binary (e.g. ArduCopter.elf) from the Downloads page [here](/downloads/).

Upload the binary to Raspberry Pi by SCP or sFTP. For example, [FileZilla](https://filezilla-project.org/) is a recommended FTP software.

##Add executable authority to APM binary
Before the first time running the binary, The executable authority must be added to it.

~~~
chmod +x ArduCopter.elf
~~~

*This step is needed only for once.*

##Run APM

The -C serial port is directed to TELEM port on the board by default. So if you want to run with a UART telemetry radio, type the following in the console.

~~~
sudo ./ArduCopter.elf -B /dev/ttyAMA0
~~~

If you want to use UDP protocol via WiFi or Ethernet as the telemetry, type the following in the console. *(assume the IP address of your Ground Control Station is 192.168.1.100)*

~~~
sudo ./ArduCopter.elf -B /dev/ttyAMA0 -C udp:192.168.1.100:14550
~~~

Or use both UDP and UART telemetry radio:

~~~
sudo ./ArduCopter.elf -A udp:192.168.1.100:14550 -B /dev/ttyAMA0
~~~

The uartB is used for GPS by default, APM software will try different protocols and baudrate to detect the GPS.

The uartA & uartC are used as primary and secondary telem ports by default. The default baudrate is 115200 for uartA, and
57600 for uartC.

These configurations(usage, baudrate, etc) of uartA, B and C can be modified in Parameter Settings in Mission Planner.

Type the following to see more help of the optional parameters.

~~~
sudo ./ArduCopter.elf -h
~~~

##Setup APM autostart on boot

To start the binary automatically after Raspberry Pi booting, add the following to /etc/rc.local in Raspberry Pi. Please change the -A, -B, -C options to suit your setup.

~~~
sudo ./home/pi/ArduCopter.elf -A udp:192.168.1.100:14550 -B /dev/ttyAMA0 > /home/pi/startup_log &
~~~

##Setup battery monitor
To use a battery monitor on RasPilot is as same as on Pixhawk. The config parameters are same.

Here is a screen shot of battery monitor parameters.
<img src="{{ site.url }}/images/pages_battery_monitor.png">

##Compass Calibration tip
The big metal USB sockets on Raspberry Pi B+ & 2B could cause soft-iron effect (not that notable on RPi A+). So it strongly recommended to do soft-iron cabration. [Here is the tutorial](/softiron_calibration/).

##Clear the "EEPROM"
On APM2, the config parameters are stored in a EEPROM chip. But on RasPilot there is actually no EEPROM on the board. All the parameters are stored as a file in the Linux file system, likes <strong>"/var/APM/ArduCopter.stg"</strong> for copter, or <strong>"/var/APM/ArduPlane.stg"</strong> for plane.

To clear the "EEPROM", type the following in the RPi console.

~~~
sudo rm /var/APM/ArduCopter.stg
~~~

Also you can do a reset in Mission Planner as the normal way.

##Download logs via FTP
In Raspberry Pi, the flight logs are stored as files in Linux file system. Getting logs in Mission Planner in a normal way is fine but slowly. A better way to download logs is via FTP.

Find the logs in <strong>/var/APM/logs</strong>

##Other configurations
Most of the config procedures are as same as the other APM-running Hardwares. It's strongly recommended to read the APM documents carefully. For APM docments, please visit [http://ardupilot.com](http://ardupilot.com)

</div><!-- /.medium-8.columns -->
</div><!-- /.row -->
