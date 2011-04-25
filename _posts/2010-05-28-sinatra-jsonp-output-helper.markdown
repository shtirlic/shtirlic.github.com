---
layout: post
title:  JSONP output helper for Sinatra
tags: [ruby, sinatra, json, jsonp, jquery]
---

Sinatra framework is an excellent start for anybody who wants to make own backend service. If you are using jQuery on frontend and 
it's [jQuery.getJSON()](http://api.jquery.com/jQuery.getJSON) method you can do crossdomain requests 
to your Sinatra application with JSONP callbacks. To be able to do this your service should return JSONP data. I tried to make things straightforward 
and wrote simple Sinatra extension that outputs proper JSONP response. 

The helper is pretty simple, just pass the object to jsonp method and it will return proper JSONP response if any callbacks were
detected in request, instead it will output the plain JSON. Also if you want to define your own custom callback name you can pass
the second string param with your preferred callback name.


Installation
------------

{% highlight bash %}
sudo gem install sinatra-jsonp
{% endhighlight %}


Usage
-----

Classic:

{% highlight ruby%}
    require "sinatra"
    require "sinatra/jsonp"

    get '/hello' do
      data = ["hello","hi","hallo"]
      JSONP data      # JSONP is an alias for jsonp method
    end

    # define your own callback as second string param
    get '/hi' do
      data = ["hello","hi","hallo"]
      jsonp data, 'functionA'
    end

    # same with symbol param
    get '/hallo' do
      data = ["hello","hi","hallo"]
      jsonp data, :functionB
    end
{% endhighlight %}

Modular:

{% highlight ruby%}
    require "sinatra/base"
    require "sinatra/jsonp"

    class Foo < Sinatra::Base
      helpers Sinatra::Jsonp

      get '/' do
        data = ["hello","hi","hallo"]
        jsonp data
      end
    end
{% endhighlight %}


Links
-----

* [jQuery](http://jquery.com)
* [Sinatra](http://www.sinatrarb.com)
* [Sinatra JSONP output helper](http://github.com/shtirlic/sinatra-jsonp)



