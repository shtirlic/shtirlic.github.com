---
layout: post
title: Simple Daemon for lock and unlock macOS with Yubikey
tags: [yubikey, mac, osx, macos, lock, key, security, daemon]
published: true
---

# yubikeylockd

Simple daemon for locking and unlocking OS X with Yubikey.

## Install

Via Homebrew formula:

{% highlight bash %}
 brew install https://raw.githubusercontent.com/shtirlic/yubikeylockd/master/yubikeylockd.rb
{% endhighlight %}

Manual install:

{% highlight bash %}
 git clone https://github.com/shtirlic/yubikeylockd.git
 make clean && make
{% endhighlight %}

## Additional requirements
  * [YubiKey using the native smart card (PIV) mode](https://www.yubico.com/why-yubico/for-businesses/computer-login/mac-os-login/)
  * Require password *immediately* after sleep or screen saver begins
  ![](http://i.imgur.com/URXUukP.png){: height="200px" }

## How it works

When you attach Yubikey for the first time launchctl will run yubikeylockd daemon
that will simply monitor the state of the Yubikey USB devices.
Daemon based on the sample provided by Apple for IOKit development.

It does two things:
* when device is attached it makes activity via
`IOPMAssertionDeclareUserActivity` call to turn screen on
* after device is detached it uses `IORequestIdle` to put display to sleep and (if you configured it) also locks the OS X


Links
-----
* [Github yubikeylockd project](https://github.com/shtirlic/yubikeylockd)
