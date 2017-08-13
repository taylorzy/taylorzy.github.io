---
layout: post
title: Mercurial Behind Proxy
---

<h2 class="lightBlue">{{ page.title }}</h2>

<p class="description">{{ page.date | date_to_string }}</p>

In command line:
{% highlight text %}
hg --config http_proxy.host=192.168.1.1:8080 --config http_proxy.user=Vad1mo --config http_proxy.passwd=secret clone https://bitbucket.org/Vadimo/test
{% endhighlight %}

In mercurial.ini:
{% highlight text %}
[http_proxy]
host = 192.168.1.1:8080
;port = 8080
user = Vad1mo
passwd = internet 
{% endhighlight %}

If get the below error, means system default proxy setting(IE) is different with mercurial's proxy setting:
abort: error: [SSL: UNKNOWN_PROTOCOL] unknown protocol (_ssl.c:581) 