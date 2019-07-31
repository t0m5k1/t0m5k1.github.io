---
layout: post
title: Browser Privacy Part 2
date:   2017-02-21 11:07
description: Further advice on how to retain privacy when browsing online
comments: true
toc: true
tags:
 - PC
 - Linux
 - Windows
 - Security
 - Privacy
---


In part 1 I covered ways to use your browser in such a way as to create a “walled garden” for each of the popular websites you visit in an effort to block any and all tracking. This part I shall cover further ways to protect yourself online from either broad snooping, data leaking, mitigating metadata leaks via obfuscation and even the blocking of adverts and general website password security.

So to begin with the most paranoid thing you could do is to boot up the latest copy of a live linux cd called [Tails](https://tails.boum.org/) this is a full linux installation on a cd and uses [tor browser](https://www.torproject.org/projects/torbrowser.html.en) as it’s default browser. WHOA what the hell is a tor browser? well please click the link they do a better job of explaining it than me but it is a way to connect to the internet that will make you appear anonymous.

## Dispelling Myths
Currently you might have heard some bad press for Tor but come on let’s face it if we are going to allow reports of nasty people doing nasty things with something stop us from using something then you better turn off your TV, PC, Phone, Mobile, Games Console, never use a Train, Car, Plane etc.
Every part of life has been exploited to the hilt by bad people and believe me if sick child porn gets you worried then never come on the normal internet coz it is still on there you just don’t know about it.

### The Crux
So with all the myths dispelled let’s get on with the article, to begin with we will start with a normal browser install and what to use.
Whether I run Firefox or Chrome I always install the following 3 extensions:

#### [uBlock Origin](https://github.com/gorhill/uBlock/)
uBlock Origin is NOT an “ad blocker”: it is a [wide-spectrum blocker](https://github.com/gorhill/uBlock/wiki/Blocking-mode) — which happens to be able to function as a mere “ad blocker”. The default behavior of uBlock Origin when newly installed is to block ads, trackers and malware sites.

#### LastPass
This is a password storage platform however they have been hacked and now there is an alternative. If you want to use this you'll have to search for it as I no longer endorse them.

#### [Bitwarden](https://bitwarden.com/)
Essentially this does the same as LastPass Premium but for free, You can also host your own storage server as it is open source software. If you have the skills you too can also contribute your code to the project via [their github](https://github.com/bitwarden)

#### [HTTPS Everywhere](https://www.eff.org/https-everywhere)
This enforces all websites to use HTTPS and will block those which do not.

#### [EFF Privacy Badger](https://www.eff.org/privacybadger)
Similar to Ghostery, Privacy Badger is a browser add-on that stops advertisers and other third-party trackers from secretly tracking where you go and what pages you look at on the web.  If an advertiser seems to be tracking you across multiple websites without your permission, Privacy Badger automatically blocks that advertiser from loading any more content in your browser.  To the advertiser, it's like you suddenly disappeared.

I used to use ghostery but I dropped that along with AdBlock+ and swapped them for uBlock Origin as that is what is called a “Wide Spectrum Blocker” which has the ability to block adverts. It uses what we call “Block Lists” to achieve it’s goal and you basically select the lists you want active and whitelist the ones you don’t want to be affected (IE: banking sites).

With all of those installed in your browser you should be set but if you use firefox you could go further by changing the following settings. These are all accessible via the about:config page:
>
{:.filename}
{% highlight bash %}
network.proxy.socks_remote_dns = true
browser.search.suggest.enabled = false
layout.css.visited_links_enabled = false
network.http.sendRefererHeader = 0
geo.enabled = false
browser.display.use_document_fonts = 0
{%endhighlight%}

Go to [this page](http://kb.mozillazine.org/Firefox_:_FAQs_:_About:config_Entries) for a full explanation of those and more settings.
You can go further by adding even more extensions but remember the more you have the more you are going to break website functions and the more memory the browser is going to consume, I will not provide links to them as you should be able to find them from the relevant webstore for your browser:

Cookieculler – Gives you total control over cookies
RequestPolicy – Gives you control over which 3rd party parts of site load
NoScript – Blocks all Java Script
Certificate Patrol – Give you control over what certificates to allow

Most of the above might appear to be overkill but depending on what you are doing and want to achieve you might want to add them but many will find these break their favorite sites so try it and learn it then make up your mind.
Many of you reading this should also be aware that flash is now blocked by default in the main 2 browsers but many common sites still force you to use it, in this instance I tend to send a rather shitty email to the webmaster of the site requesting they move to HTML5/CSS3 and drop all of the flash elements of their site due to the inherent security flaws it contains and the slow speed at which Adobe fix them. Therefore I suggest you install [Better privacy](https://addons.mozilla.org/en-US/firefox/addon/betterprivacy/) as it will give you greater control and probably less to delete in your next BleachBit run lol


Next we want to adjust the fingerprint of the actual browser, the biggest one is the user-agent. Click [HERE](http://www.useragentstring.com/) to see yours and give you an in depth explanation of what one is also what they are used for.

Now we want to be able to change ours to something less unique and something more common, much the same as we group ourselves with like minded strangers so it makes being sociable easier by way of giving ourselves something to talk about. So we use the following extension to do just that:

#### [User Agent switcher](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/)
Ok so you installed it now what, well it comes with 3 groups of buttons to click so you can “become” different devices, browsers and or operating systems but there are lots more, many are [listed here](http://techpatterns.com/downloads/firefox/useragentswitcher.xml) but that may well be overkill to the basic user and so I share my own:

>
{:.filename}
{% highlight bash %}
Mozilla/5.0 (Windows NT 6.1; WOW64; rv:45.0) Gecko/20100101 Firefox/45.0
{%endhighlight%}
This basically tells the server I am firefox 45 on windows 7 currently is the most common user-agent seen in the wild, there are many sites out there so just do a search for “common user agent” and you will get enough sites to make a good judgement on the best one to use.

 

Now you might be asking why all this tom? Well the reason for me mentioning them is because this makes up the part of your communications on the internet that has come to be known as “metadata” the little breadcrumbs you leave on servers as you go browsing from site to site, to get a good idea of your fingerprint click here it is a great site provided by the wonderful EFF who fight daily to ensure your real online/digital privacy rights are protected and ensured.

You can also utilise an internal DNS server, this is beyond the capability of many but I find the DNS system a true masterpiece even if it is used for Ddos amplification that in itself shows how much of a wonderful system it is and loved learning all about it but it is a good way to avoid many blocks ISP’s put on you and also a good way to circumvent DNS censorship which unfortunately is getting more and more prolific but for those less inclined to install and administer NSC DNS or BIND9 here is a list of open DNS server (note this is unmaintained and might be old)


These 2 are provided to offer malware protection and speed but may not be so anti-censorship as others:

Dnsadvantage:
>
{:.filename}
{% highlight bash %}
 156.154.70.1
 156.154.71.1
{%endhighlight%} 
OpenDNS (NOTE: OpenDNS provide a voulntary censorship service and they're now owned by Cisco):
>
{:.filename}
{% highlight bash %}
 208.67.222.222
 208.67.220.220
{%endhighlight%} 
The following DNS servers may not be anti-censorship due to them bowing to the might of a DCMA:
Google:
>
{:.filename}
{% highlight bash %}
 8.8.8.8 
 8.8.4.4
{%endhighlight%}
Norton free dns server list:
>
{:.filename}
{% highlight bash %}
 198.153.192.1
 198.153.194.1
{%endhighlight%}
GTEI DNS (now Verizon):
>
{:.filename}
{% highlight bash %}
 4.2.2.1
 4.2.2.2
 4.2.2.3
 4.2.2.4
 4.2.2.5
 4.2.2.6
{%endhighlight%} 
ScrubIt:
>
{:.filename}
{% highlight bash %}
 67.138.54.100
 207.225.209.66
{%endhighlight%} 
anti-censorship DNS servers:
 >
{:.filename}
{% highlight bash %}
 85.88.19.10 (German Xail.net) sehr schnell!
 85.88.19.11 (German Xail.net)
 87.118.100.175 (German Privacy Foundation e.V.)
 94.75.228.28 (German Privacy Foundation e.V.)
 62.141.58.13 (German Privacy Foundation e.V.)
 62.75.219.7 (German Privacy Foundation e.V.) 
 85.214.73.63 (FoeBuD e.V.)
 212.82.225.7 (ClaraNet)
 212.82.226.212 (ClaraNet)
 213.73.91.35 (Chaos Computer Club Berlin) +1
 58.6.115.42 (OpenNIC, Australien)
 58.6.115.43 (OpenNIC, Australien)
 119.31.230.42 (OpenNIC, Australien)
 200.252.98.162 (OpenNIC, Brasilien)
 217.79.186.148 (OpenNIC, Deutschland)
 82.229.244.191 (OpenNIC, Frankreich)
 216.87.84.211 (OpenNIC, USA)
 2002:d857:54d2:2:20e:2eff:fe63:d4a9 (OpenNIC, IPv6 USA)
 2001:470:1f07:38b::1 (OpenNIC, IPv6 USA)
 2001:470:1f10:c6::2 (OpenNIC, IPv6 USA)
 66.244.95.20 (OpenNIC, USA)
 204.152.184.76 (f.6to4-servers.net, ISC)
 2001:4f8:0:2::14 (f.6to4-servers.net, IPv6, ISC)
 194.150.168.168 (dns.as250.net; anycast DNS!)
 80.237.196.2 (Erdgeist)
 194.95.202.198 (UDK Berlin)
 88.198.130.211 (Dataflash)
 78.46.89.147 (ValiDOM)
 129.206.100.126 (URZ Uni Heidelberg)
 79.99.234.56 (justnet.ch, Schweiz)
 156.154.70.22 (Comodo Secure DNS)
 156.154.71.22 (Comodo Secure DNS)
 85.25.149.144 (Freie DNS-Server)
 87.106.37.196 (Freie DNS-Server)
 88.198.24.111 (jali/CCCHB)
{%endhighlight%}

#### Encryption
Now we get deeper, you might have noticed that this website is using HTTP this is because my hoster is trying to charge huge prices for certificates and a static ip address therefore I am looking at other alternatives but until then this will do.
The reason I endorse the use of HTTPS is because less of your breadcrumbs get left on the servers you visit, the “conversations” you have with servers are all private meaning it is harder for others to sniff your traffic to get your important information.

Currently your TV will have you believe that only the nasty people use encryption and therefore it is bad and needs to be stopped or it needs to have a backdoor built into it so that you ever friendly government department of security (GCHQ/NSA) can take a look and sniff at what you are doing!
On the other hand your bank is telling you that you should only use their secure connections to communicate with them to protect your pin number and password that you use to get access to their very secure systems.

So why on earth are you going to give up your privacy when communicating to your bank to what is effectively a group of strangers whom you have never met let alone uttered a single word to? Yes they do work for the Gov. but they are just that employee’s who can and do get fired for what ever reason and lets just say one day Joe Schmoe GCHQ analyst gets fired for something petty but has been sat there at his desk for the past year looking over what prism has dumped into a database and has your bank access credentials along with 200 others and decides screw you GCHQ I’m gonna go sell these on that hidden website i discovered for a couple of grand! …two days later your bank is empty and none of your bills get paid.

That is a simple scenario but it would be possible and if you continue to think encryption needs to be controlled blah blah just email me all your passwords please to my email address.

There are also people out there who use a VPN with Tor Browser for that added extra piece of mind, these days VPN’s are becoming quite cheap but again due to the bad press encryption has received many sites like netflix and amazon will complain when you access their servers via Tor and/or a VPN as they like to know you are who you say and logging in is not enough and don’t even think about using your netflix when on holiday unless that is your VPN endpoint is actually your home network then it will work …oopsie did I just give you a clue!!

[HERE](https://torrentfreak.com/vpn-anonymous-review-160220/) is a great list of VPN providers that I would seriously consider using if I wanted a VPN, the list is comprised in such a way that the one at the top of the list basically has amnesia towards it’s customers and so when pressed will only give the most basic of information about you because they do not have the rest!
If you do use a VPN and are doing things which some may consider questionable the consider moving to one on that list.

#### Deeper Still
So the simplest most easiest way to access the web in an anonymous way is by using [Tor Browser](https://www.torproject.org/projects/torbrowser.html.en) many would argue that is overkill but I say many reporters and corporate workers use it and the more people who use it the better it gets and the faster the network becomes also it is sort of like a poor mans VPN (sorry to use the term) but if you use it to access normal sites like this one my logs will show you connecting from sweden, russia, ukraine, luxembourg, poland, germany, usa where ever because the exit node is random for each url/tab.

Also Tor Browser comes preinstalled with many of the extensions I mention above but aside from that these days we need to be able to control how we interact on the web and we also need to ensure that dumb ass laws and borders that control our movement around the globe are not enforced on the internet as it was never designed with that in mind which is why now we need these things to effectively fix what legislation has broken.

NOTE: In 2017 there has been mucho chato about TOR exit relays popping up all over the place that are compromised and run by Gov. officials, this may or may not be true but if you are going to use it my current advice would be to just use it as a layer in an ever growing onion because at the end of the day it is just another proxy so if all you want/need to do is send a plain text message you can easily add another layer without me having to explain.

There is also the alternative to Tor which is [i2p](https://geti2p.net/) but alas there is no preconfigured browser for it so you will need to install it and then connect to it much in the same way as a proxy. I may well create an article for it in the coming months but for now get the information you need from the provided link.

Now what comes next is probably what nearly all of the basic and some advanced users would not even bother doing just because it can be tricky but also because they see no point but for completeness and for the love of knowledge here goes.

#### MAC Spoofing
…this is changing your unique MAC address to a random address (not 00:00:00:00:00:00 or AA:AA:AA:AA:AA:AA, keep it legit-looking).
Why would I do that Tom?
Well some people who use a modem may not want their MAC address to remain as it is and other may want to change the firewall MAC address for other reasons, remember not everything we can do is only done for nefarious reasons and to lessen our trail of breadcrumbs is better even still.

To do this on linux follow these steps:

install macchanger (this will differ depending on your distro)
then type

 >
{:.filename}
{% highlight bash %}
sudo macchanger -A eth0
{%endhighlight%}
NOTE: eth0 is the interface, use the following to show all interfaces, don’t use lo0, that is a loopback interface!!

 >
{:.filename}
{% highlight bash %}
sudo ip link show
{%endhighlight%}
The output will be a list of interfaces as follows:
 >
{:.filename}
{% highlight bash %}
lo : local loopback
wlan0: wireless interface
eth0: ethernet interface
tap or tun0: VPN interface.
{%endhighlight%}
If you use wlan then you could use something like:

 >
{:.filename}
{% highlight bash %}
sudo ifconfig wlan0 down
sudo ifconfig wlan0 hw ether 01:42:0a:82:5f:92
sudo ifconfig wlan0 up
{%endhighlight%}
You can also do this every boot automatically. In debian based systems you can add the following script and chmod +x in /etc/network/if-pre-up.d/macchanger (In other systems you may need to create a systemd script)

 >
{:.filename}
{% highlight bash %}
#!/bin/sh
MACCHANGER=/usr/bin/macchanger
ifconfig eth0 down
macchanger -A eth0
ifconfig eth0 up
{%endhighlight%}
Again replace eth0 with the interface you use to connect to the net.

#### Mac OS X

Paste the following into Terminal (Applications/Utilities/Terminal.app):

 >
{:.filename}
{% highlight bash %}
sudo su /System/Library/PrivateFrameworks/Apple80211.framework/Versions/Current/Resources/airport /usr/sbin/airport -z
sudo ifconfig en1 ether 00:00:00:00:00:00
{%endhighlight%}
Reconnect to a wireless network, for wired connections change ‘en1’ to ‘en0’

#### BSD

Type the following:

 >
{:.filename}
{% highlight bash %}
ifconfig xl0 down
ifconfig xl0 link 00:00:00:AA:AA:AA
ifconfig xl0 up
{%endhighlight%}
Obviously you will need to ascertain your nic first.

#### Windows 2000/XP

Method 1:

This is depending on the type of Network Interface Card (NIC) you have. If you have a card that doesn’t support Clone MAC address, then you have to go to second method.

Go to Start->Settings->Control Panel and double click on Network and Dial-up Connections.
Right click on the NIC you want to change the MAC address and click on properties.
Under “General” tab, click on the “Configure” button
Click on “Advanced” tab
Under “Property section”, you should see an item called “Network Address” or “Locally Administered Address”, click on it.
On the right side, under “Value”, type in the New MAC address you want to assign to your NIC. Usually this value is entered without the “-” between the MAC address numbers.
Goto command prompt and type in “ipconfig /all” or “net config rdr” to verify the changes. If the changes are not materialized, then use the second method.
If successful, reboot your system.

Method 2:

This should work on all Windows 2000/XP systems

Go to Start -> Run, type “regedt32” to start registry editor. Do not use “Regedit”.
Go to “HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\ Control\Class\{4D36E972-E325-11CE-BFC1-08002BE10318}”. Double click on it to expand the tree. The subkeys are 4-digit numbers, which represent particular network adapters. You should see it starts with 0000, then 0001, 0002, 0003 and so on.
Find the interface you want by searching for the proper “DriverDesc” key.
Edit, or add, the string key “NetworkAddress” (has the data type “REG_SZ”) to contain the new MAC address.
Disable then re-enable the network interface that you changed (or reboot the system).

If all else fails try the program [Etherchange](http://ntsecurity.nu/toolbox/etherchange/) NOTE: you browser may give a warning about malicious programs, this is due to the nature of what this program can do!!!

#### Windows 9x 
(Seriously if you are reading this and use this OS I’d give you the slow clap!!)
Use the same method as Windows 2000/XP except for the registry key location is “HKEY_LOCAL_MACHINE\System\ CurrentControlSet\Services\Class\Net” and you must reboot your system.

Keep in mind that, even if you spoof your mac and you are behind a router it’s the router’s mac that’s exposed, not your computers so if you want this to work you need to either change the MAC of your router (pfsense, m0n0wall allow this) or use a vpn. (Tips to firewall a vpn conn would be niceness too)

Whilst reading this article I hope you have learned of more of the options that are available to you to help protect you when browsing online whatever it is you are looking for. As a final note I would also state that I did not mention the obvious basic settings your browser provides to forgetful for a reason one is that I hope you have already prior to reading this configured your browser to not keep history, clear the cache on exit or have set the cache size to 1mb, only keep the cookies you want to keep (work, bank, important sites) I know I may come across as paranoid but when you work in IT and read about all the things the Gov. try to tell non techies that the security on the internet is bad and needs a back door you tend to get slightly annoyed by that premise and this article I hope serves to highlight why we need them, how to use them and dispel some myths.

So finally I say:

NEVER LOG ANYTHING, HIDE ALL YOU CAN, NEVER BE UNIQUE, OBFUSCATE, ENCRYPT, BE AWESOME
