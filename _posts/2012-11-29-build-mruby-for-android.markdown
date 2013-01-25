---
layout: post
title: Build mruby for Android
tags: [ruby, mruby, android, ndk, build, cmake, arm, toolchain  ]
published: true
---


> mruby – Minimalistic Ruby and Its Possibility
> <cite>Matz</cite>

If you like playing with cool new stuff and have Android device here is the instructions of how to build mruby for Android using Android NDK arm toolchain.
The goal was to use less custom stuff and make less modifications to original build process.

Note: These instructions are for Mac OS X. The procedure is similar for other *nix.

### mruby source
* Clone [mruby](https://github.com/mruby/mruby) from GitHub
{% highlight bash %}
git clone git://github.com/mruby/mruby.git
{% endhighlight %}


### Android NDK
* Download [latest Android NDK for Mac OS X (intel)](https://developer.android.com/tools/sdk/ndk/index.html)
* Unarchive it to home `~/android-ndk-r8c`

{% highlight bash %}
# Make symlink
ln -s ~/android-ndk-r8c ~/android-ndk
# Make custom standalone toolchain as described here (~/android-ndk/docs/STANDALONE-TOOLCHAIN.html)
cd ~/android-ndk/
build/tools/make-standalone-toolchain.sh --platform=android-14 --install-dir=/tmp/android-14-toolchain
# Export var used by android toolchain cmake file
# Add this line to your ~/.profile file for future use
export ANDROID_STANDALONE_TOOLCHAIN=/tmp/android-14-toolchain
{% endhighlight %}

### CMake
* Install cmake using [homebrew](http://mxcl.github.com/homebrew/) `brew install cmake`
* Put [android toolchain cmake](http://code.google.com/p/android-cmake/source/browse/toolchain/android.toolchain.cmake) file into `cmake/modules` in mruby source tree
* Put my [mruby osx android toolchain cmake](https://gist.github.com/4170066) file into the root of the mruby source tree

{% highlight bash %}
cd mruby/build
# Run cmake and make
cmake -DCMAKE_TOOLCHAIN_FILE=../Toolchain-OSX-androideabi.cmake ..
make -j8
{% endhighlight %}

### Optional
* Run `make package` to make archive
* Put it on sdcard/internal storage, unzip and run it on your device



Links
-----
* [mruby GitHub project](https://github.com/mruby/mruby)
* [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html)
* [homebrew](http://mxcl.github.com/homebrew/)
* [CMake](http://www.cmake.org/)
* [android-cmake project](https://code.google.com/p/android-cmake/)
