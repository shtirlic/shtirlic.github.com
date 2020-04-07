---
layout: post
title:  Clear Linux on Dell XPS 7390 2 in 1
tags: [dell, xps, 7390, 2in1, clearlinux, wifi, gnome, fix, issues, i915, mesa]
---

Almost all works out of the box on the current Clear Linux version `32660` with kernel `Linux arazu 5.5.10-921.native #1 SMP Wed Mar 18 16:03:14 PDT 2020 x86_64 GNU/Linux`
with some exceptions:
  - No camera
  - No fingerprint
  - No WiFi
  - Pereodic Gnome freeze for ~20 seconds due ti [id915/mesa bug](https://gitlab.freedesktop.org/mesa/mesa/issues/2183)

WiFi fix
------------

{% highlight bash %}
ln -s /lib/firmware/iwlwifi-Qu-c0-hr-b0-48.ucode /lib/firmware/iwlwifi-Qu-c0-hr-b0-52.ucode
{% endhighlight %}

=>reboot


Gnome Freeze fix
----------------

Disable subpixel font antialiasing via dconf editor/settings/coomand line

{% highlight bash %}
gsettings set org.gnome.settings-daemon.plugins.xsettings antialiasing 'grayscale'
gsettings set org.gnome.settings-daemon.plugins.xsettings hinting 'medium'
{% endhighlight %}


Additional Notes
----------------

Enable S3 sleep
---------------

- Disable `signs of life` in bios for normal s3 sleep. 
- Add `mem_sleep_default=deep` to the `/etc/kernel/cmdline` then `sudo clr-boot-manager update`  
- =>reboot

Disable tap and drug for touchpad
----------------

{% highlight bash %}
gsettings set org.gnome.desktop.peripherals.touchpad tap-and-drag false
{% endhighlight %}

Enable new IWD wireless backend for NetworkManager
----------------

Put it to `sudo vim /etc/NetworkManager/NetworkManager.conf`
{% highlight ini %}
[device]
wifi.backend=iwd
{% endhighlight %}

then run
{% highlight bash %}
sudo swupd bundle-add iwd
sudo systemctl stop wpa_supplicant.service
sudo systemctl restart NetworkManager.service   
{% endhighlight %}

=>reconnect to WiFi networks

Links
-----

* [Clear Linux](https://clearlinux.org/)



