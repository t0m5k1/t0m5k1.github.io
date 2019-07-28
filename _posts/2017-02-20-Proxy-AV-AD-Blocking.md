---
layout: post
title: Proxy+AV+IP Blocking
date:   2017-02-19 11:07
description: Squid Proxy with child AV scanning and AD/IP Blocking
comments: true
tags:
 - PC
 - Linux
 - Security
---

Conventions used in this article:
$ = normal linux user
\# = root user

Install squid, havp, clamav, ipblock and their dependencies:

>bash
{:.filename}
{% highlight bash %}
sudo aptitude install squid havp clamav ipblock
- or -
sudo pacman -Ss squid havp clamav ipblock
{% endhighlight %}
NOTE: Not all distros have ipblock in their software repositories/databases if this is your case find an alternative or compile from source.

configure squid to your preferences BUT ensure you add the following:

>namo \ vim
{:.filename}
{% highlight bash %}
cache_peer 127.0.0.1 parent 8080 0 no-query no-digest no-netdb-exchange default
{% endhighlight %}

configure havp as follows:

>nano \ vim /etc/havap/havp.conf
{:.filename}
{% highlight bash %}

USER havp
GROUP havp
DAEMON true
PIDFILE /var/run/havp/havp.pid
SERVERNUMBER 20 # please adjust yourself
MAXSERVERS 100 # please adjust yourself
ACCESSLOG /var/log/havp/access.log
ERRORLOG /var/log/havp/havp.log
USESYSLOG false
SYSLOGNAME havp
SYSLOGFACILITY daemon
SYSLOGLEVEL info
LOG_OKS true
LOGLEVEL 1
SCANTEMPFILE /var/spool/havp/havp-XXXXXX
TEMPDIR /var/tmp
DBRELOAD 60
TRANSPARENT false
FORWARDED_IP true
PORT 8080
BIND_ADDRESS 127.0.0.1
TEMPLATEPATH /etc/havp/templates/en
ENABLECLAMLIB true
CLAMDBDIR /var/lib/clamav
ENABLECLAMD false
ENABLEFPROT false
ENABLEAVG false
ENABLEAVESERVER false
ENABLESOPHIE false
ENABLETROPHIE false
ENABLENOD32 false
ENABLEAVAST false
ENABLEARCAVIR false
ENABLEDRWEB false
{% endhighlight %}

now at this point consider making a tmpsfs of 512-1024Mb for /var/tmp and setup /tmp as a sym link, Some distros do this by default and others have /dev/shm setup as a ramdrive but to be honest i preffer this way as you have created a fixed size for virus scanning & you know for certain that /tmp and /var/tmp will be cleared out on reboot:

>bash
{:.filename}
{% highlight bash %}
$ sudo -s
# mkdir /tmp.old; chmod 777 /tmp.old
# cp -rav /tmp/* /tmp.old; rm -r /tmp
# mount -t tmpfs -o size=256M tmpfs /var/tmp/
# ln -s /var/tmp /tmp
# cp -rav /tmp.old /tmp; rm -r /tmp.old
{% endhighlight %}

if you want this to be a transparent setup the following iptables rules:

>bash
{:.filename}
{% highlight bash %}
# iptables -t nat -A PREROUTING -j REDIRECT -p tcp -i eth0 -s 192.168.0.0/24 -dport 80 -to-ports 3128
# iptables -t nat -A POSTROUTING -j MASQUERADE -p tcp -s 192.168.0.0/24 -o eth1
{% endhighlight %}
update clam:

>bash
{:.filename}
{% highlight bash %}
# freshclam
{%endhighlight%}
NOTE: you may want to have this update manually so make sure you edit /etc/clamav/freshclam.conf to run as daemon, then when you run the command above it will jump to background after initial update.

start services:
>bash
{:.filename}
{% highlight bash %}

# squid -k reconfigure
# /etc/init.d/havp force-reload
# /etc/init.d/ipblock start
- or -
# /etc/init.d/squid restart
# /etc/init.d/havp restart
# /etc/init.d/ipblock restart
- or -
# service squid start; service havp start; service ipblock start
{%endhighlight%}
All done, all you test with eicar file download and you should see the havp access denied page indicating a virus was found
