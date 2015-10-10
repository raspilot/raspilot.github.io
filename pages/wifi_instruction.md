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

##Recommended wireless devices

##host an AP on USB wireless dongle

##USB WiFi on the air & router on the Ground

##High power wireless net bridge

##Control Ground Station (CGS) on phone

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
