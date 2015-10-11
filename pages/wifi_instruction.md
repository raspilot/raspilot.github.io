---
layout: page-fullwidth
title: "WiFi Instruction"
subheadline: "How to use RasPilot"
teaser: "The documentation is a work in progress..."
permalink: "/wifi_instruction/"
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

##2.4GHz or 5GHz?
There is  a bunch of 2.4GHz USB WiFi dongles you can find working on Raspberry Pi. Or using a WiFi rounter connecting with Ethernet port on Raspberry Pi is an alternative idea. However, we know most of RC systems work on 2.4GHz spectrum as well. And to ensure the robust, most of them transmit on almost all channels of 2.4GHz spectrum, which seriously interfere with WiFi systems.

One solution is to hack the RC controller to keep away from some of the WiFi channels. Here is  an instruction on [befinitiv's blog](https://befinitiv.wordpress.com/2015/08/26/enable-2-4ghz-rc-systems-to-work-with-2-4ghz-video-systems/).

But we still have a clean place: 5GHz. Fewer WiFi devices are working on 5GHz spectrum, and normally no RC controller uses 5GHz. We should get a good performance on 5GHz. And it's strongly recommended to use 5.8GHz channnels on WiFi FPV and telemetry.

##Recommended wireless devices

###USB dongle
By now, RTL8812AU is the only choice of 5GHz chipset working on Raspberry Pi. We can find supported dongles at [WikiDevi](https://wikidevi.com/wiki/Special:Ask?title=Special%3AAsk&q=[[Chip1+model::RTL8812AU]]&po=%3FInterface%0D%0A%3FForm+factor=FF%0D%0A%3FInterface+connector+type=USB+conn.%0D%0A%3FFCC+ID%0D%0A%3FManuf%0D%0A%3FManuf+product+model=Manuf.+mdl%0D%0A%3FVendor+ID%0D%0A%3FDevice+ID%0D%0A%3FChip1+model%0D%0A%3FSupported+802dot11+protocols=PHY+modes%0D%0A%3FMIMO+config%0D%0A%3FOUI%0D%0A%3FEstimated+year+of+release=Est.+year&eq=yes&p[format]=broadtable&order[0]=ASC&sort_num=&order_num=ASC&p[limit]=500&p[offset]=&p[link]=all&p[sort]=&p[headers]=show&p[mainlabel]=&p[intro]=&p[outro]=&p[searchlabel]=%E2%80%A6+further+results&p[default]=&p[class]=sortable+wikitable+smwtable). And the driver is compiled into the [lastest Linux image](/downloads/).

To achieve high sensitivity, you could choose the following dongles:

* [ALFA Network AWUS036AC](http://www.amazon.com/dp/B00MX57AO4)
* [ALFA Network AWUS036ACH](http://www.amazon.com/dp/B00VEEBOPG)

###WiFi router

###High power net bridge

##Ways to connect Raspberry Pi and Ground Station

###host an AP on USB wireless dongle
The native hostapd program in Raspberry Pi image does not support 5GHz AP mode. So I compiled from source code of a [patched hostapd](https://github.com/pritambaral/hostapd-rtl871xdrv) on Github. You could download the compiled hostapd binary in the [Download Page](/downloads/). Then extract it on Raspberry Pi.

Copy hostapd to install the hostapd.

~~~
sudo cp hostapd /usr/local/bin
~~~

Change the configurations in <strong>hostapd.conf</strong>. Then start hostapd to host an AP. You would see debug info.

~~~
sudo hostapd -d hostapd.conf
~~~

You could also edit the <strong>/etc/rc.local</strong> file to make it automatically start on boot. Add the following line before <strong>exit 0</strong>.

~~~
sudo hostapd /home/pi/hostapd.conf &
~~~

###USB WiFi on the air & router on the Ground

###High power wireless net bridge

##Ground Control Station (GCS) on phone
Tower (Droid Planner) is an open-source groun station running on Android devices, with beautiful user interface. If support connection to droid via USB telemetry, bluetooth, or UDP from network.

In a typical application, you could connect your phone to the AP hosted by dongle, choose the UDP mode in the setting, then enjoy the flight. The default UDP port is 14550.

Download the lastet Tower from [Google Play](https://play.google.com/store/apps/details?id=org.droidplanner.android).

<img src="{{ site.url }}/images/pages_droid_planner.png">

##Get more current supply from USB
The default max current supplied from USB is 600mA. However, you can change the settings to get 1.2A max supply, to drive more power demanding devices. (warning: be careful to avoid demage to Raspberry Pi)

Edit <strong>/boot/config.txt</strong>. Add the following line to the end of the file.

~~~
max_usb_current=1
~~~

Then reboot Raspbeery Pi to make it work.

~~~
sudo reboot
~~~

</div><!-- /.medium-8.columns -->
</div><!-- /.row -->
