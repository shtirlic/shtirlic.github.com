---
layout: post
title:  Clear Linux on Dell XPS 7390 2 in 1
tags: [dell, xps, 7390, 2in1, clearlinux]
---

Almost all works out of the box on the current Clear Linux version `32660` with kernel `Linux arazu 5.5.10-921.native #1 SMP Wed Mar 18 16:03:14 PDT 2020 x86_64 GNU/Linux`
with some exceptions:
  - No camera
  - No fingerprint
  - No WiFi

WiFi fix
------------

{% highlight bash %}

ln -s /lib/firmware/iwlwifi-Qu-c0-hr-b0-48.ucode /lib/firmware/iwlwifi-Qu-b0-hr-b0-50.ucode

{% endhighlight %}

and Reboot


Additional Notes
----------------

Disable `signs of life` in bios for normal s3 sleep and add 
`mem_sleep_default=deep` to the `/etc/kernel/cmdline`

and Reboot

Also I use secureboot with deploy mode.


Links
-----

* [Clear Linux](https://clearlinux.org/)



