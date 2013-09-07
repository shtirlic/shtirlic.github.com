---
layout: post
title: Mozilla Sync server under Nginx
tags: [nginx, mozilla, firefox, sync, server]
published: true
---

If you want to run Mozilla Sync server behind your Nginx installation, here is the simple config.


{% highlight bash %}
upstream mozilla_sync {
        server localhost:5000 fail_timeout=0;
}
{% endhighlight %}

{% highlight bash %}
server {
        # ... some your stuff
        location /sync/ {
                rewrite /sync/(.*) /$1 break;
                proxy_pass http://mozilla_sync;
        }
}
{% endhighlight %}

Remember: Please setup SSL/TLS on your Nginx server for privacy and security.

Links
-----
* [Run your own Sync Server](http://docs.services.mozilla.com/howtos/run-sync.html)
* [Nginx Docs](http://nginx.org/en/docs/)

