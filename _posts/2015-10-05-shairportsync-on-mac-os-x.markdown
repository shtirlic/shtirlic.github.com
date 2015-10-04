---
layout: post
title: shairport-sync on Mac OS X
tags: [shairport, apple, airplay, mac, osx, homebrew]
published: true
---

Shairport Sync emulates an AirPort Express for the purpose of streaming audio from iTunes, iPods, iPhones, iPads and AppleTVs. Audio played by a Shairport Sync-powered device stays synchronised with the source and hence with similar devices playing the same source. In this way, synchronised multi-room audio is possible without difficulty. (Hence the name Shairport Sync, BTW.)

Building this on OS X is not so straightforward, so I made the [formula for homebrew](https://gist.github.com/shtirlic/d55b3ac3767a2e7f54eb) it.

Install via

{% highlight bash %}
brew install  https://gist.githubusercontent.com/shtirlic/d55b3ac3767a2e7f54eb/raw/f7395d9f8015e5441e26811ad430c1410cc7cd44/shairport-sync.rb
{% endhighlight %}

PS
Building with libsoxr, libao and dns_sd


Links
-----
* [homebrew](http://mxcl.github.com/homebrew/)
* [shairport-sync](https://github.com/mikebrady/shairport-sync)
* [AirPlay](https://en.wikipedia.org/wiki/AirPlay)
