---
layout: post
title: Installing rtl-sdr on Raspberry Pi 2
tags: [rtl-sdr, rtlsdr, rtl, sdr, raspbian, raspberry, pi, 2 ]
published: true
---

Use latest RASPBIAN based on the Debian Jessie and since Raspberry PI 2 is **armhf** architecture there are much more packages available now.  

{% highlight bash %}
sudo apt-get install libusb-1.0-0.dev librtlsdr-dev
{% endhighlight %}

Make **/etc/modprobe.d/raspi-blacklist.conf** and add the following lines:

{% highlight bash %}
blacklist dvb_usb_rtl28xxu
blacklist rtl2832
blacklist rtl2830
{% endhighlight %}

 Make **/etc/udev/rules.d/rtl-sdr.rules** and add the following lines:

 {% highlight bash %}
 # original RTL2832U vid/pid (hama nano, for example)
 SUBSYSTEMS=="usb", ATTRS{idVendor}=="0bda", ATTRS{idProduct}=="2832", MODE:="0666"

 # RTL2832U OEM vid/pid, e.g. ezcap EzTV668 (E4000), Newsky TV28T (E4000/R820T) etc.
 SUBSYSTEMS=="usb", ATTRS{idVendor}=="0bda", ATTRS{idProduct}=="2838", MODE:="0666"
 {% endhighlight %}

Restart with **shutdown -r 0** the Raspberry Pi and you are ready to use your rtl-sdr dongle.

Links
-----
* [Official Raspbian Downloads ](https://www.raspberrypi.org/downloads/raspbian/)
* [rtl_433 Application using librtlsdr to decode the temperature from a wireless temperature sensor (433.92MHz)](https://github.com/merbanan/rtl_433)
* [GNU Radio project](http://gnuradio.org/redmine/projects/gnuradio/wiki)
* [dum1090 Mode S decoder](https://github.com/antirez/dump1090)
* [rtl-sdr.com](http://www.rtl-sdr.com/)
