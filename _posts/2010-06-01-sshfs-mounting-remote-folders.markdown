---
layout: post
title: Mounting remote folders with SSHFS
tags: [sshfs, linux, filesystem, remote, mounting]
published: true
---

SSHFS is filesystem based on the SSH File Transfer Protocol (SFTP). If you have server with enabled SSH protocol it's 99% that 
this server supports SFTP out of the box. It comes very handy when you are working with remote servers and want to use favorite
text editor and environment to work with remote files.

Some of the use cases are:

* Uploading your site content
* Storing images on remote server
* Syncing files

Installing on Ubuntu
----------------------

{% highlight bash %}
sudo apt-get install sshfs
{% endhighlight %}

Using
-----

{% highlight bash %}
# create local dir in your home for remote connections
mkdir ~/external                
# create local dir that should be mapped to remote dir
mkdir ~/external/guruser.somehost   
# mount remote dir to your local dir
sshfs guruser@somehost:/home/guruser ~/external/guruser.somehost/  
{% endhighlight %}


For example: if you want to use rsync but your server doesn't have rsync installed you can always mount preferred remote directory via sshfs and sync it with rsync 
just like between local directories.


Links
-----

* [SSH Filesystem](http://fuse.sourceforge.net/sshfs.html)
* [rsync](http://samba.anu.edu.au/rsync/)
