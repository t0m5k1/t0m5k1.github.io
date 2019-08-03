---
layout: post
title: Browser Privacy Part 3
date:   2019-02-06
description: New advice on protecting privacy whilst you're online.
comments: true
toc: true
tags:
 - PC
 - Linux
 - Windows
 - Security
 - Privacy
---


In [part 2](https://tomsbox.co.uk/2017/02/Browser-Privacy-2/) I covered additional extensions and encrption methods to keep yourself as invisible as possible.

It would seem that others out there have similar ideas and have extended things further. We now have a new browser [Brave](https://brave.com) which is a fork of chromium but they have removed all the google parts and added advert blocking, tracker blocking, social button removal and TOR!

As well as being a very welcome alternative to chromium Brave also has tipping, Yes you can earn by viewing privacy-respecting ads and pay it forward to support content creators you love. They have created the [BAT](https://basicattentiontoken.org/) "Basic Attention Token" which is a form of crypto currency that you earn by viewing curated adverts in the form of website from content creators who hasve signed up to the BAT Project, Additionally you can add funds to your own BAT Wallet and via this wallet you can also pass on set amount(1,5,10) of BAT to content creator you like so long as they've signed up.
Additionally you can effectivley subscribe to a creator meaning each month your brave browser will automatically send a prefixed amount of BAT to the content provider of your choice or even multiple creators. I mentioned earlier you can add funds to your BAT wallet, This can be in the form of hard cash or even crypto from other popular crypto currencies like Etherium, bitcoin, etc.
Further information can be found over at the [BAT website](https://basicattentiontoken.org/). I think it is pretty damn amazing to be fair but as with all things new that tend to rock the boat too much you will have people who do not like it. 
Some people who sign up are finding that the revenue stream they get from BAT is too small but to be fair the rocket has only just taken off anf it is still 1 kilometer off the surface so at the moment there are few creators signed up and even less people putting real money into tokens for their wallet so the conversion rate is a bit low, at time of typing 1 BAT = 0.23629 USD.



So as you can guess I tend to use this browser as my daily driver and highly recommend you do to, additionally there is something called [Pi-Hole](http://pi-hole.net). 

[Pi-Hole](http://pi-hole.net) is essentially a DNS server with additional blocklists to stop known advertisers displaying their tracking adverts in your browser session by way of a DNS trick. This trick utilises the DNS system itself to block ads, When you make a DNS lookup for my site your PC converts tomsbox.co.uk into an IP that is routable over the internet. Think of it as your front door to the internet.
When you use Pi-Hole as your DNS server and you lookup a known advert ad.advertoser.com Pi-Hole will provide your pc with the address 127.0.0.1. The 127.0.0.1 is a rather special IP address, Firstly when used on the internet it will not route anywhere, meaning it is a black hole. To your pc it is known as "localhost" or home, so think of 127.0.0.1 as "my PC/Laptop"

So using Pi-Hole will speed up your web browsing by loading less data for a given website but will also stop you being partially tracked on the internet. Using Pi-Hole with Brave Browser is like having a saftey need behind your ad blockers built into the browser, This is especially good to do as not adverts can be blocked by Brave but also Pi-Hole is aware of known malware sites and so will block them too.

I will be covering setting up Pi-Hole in an up comming article. For now we'll continue with browsers.

[FireFox](https://www.mozilla.org/en-GB/firefox/) has also made some new changes in that it too now offers blocking and Tracking Protection, As you know some ads have hidden trackers that follow you online. It also has a new backend called Quantum which aside from doing all the fancy stuff under the cover it results in a faster experience. As well as blocking trackers it will block Cryptominers and Fingerprinters. All have relevant settings for you to change to suit how you want them to work along with the ability to choose a tracker block list which are supplied by Diconnect.
Mozilla also offer a new addon: [Facebook Container](https://addons.mozilla.org/en-US/firefox/addon/facebook-container/). This will stop Facebook tracking by isolating your Facebook identity into a separate “container” that makes it harder for Facebook to track your movements around the web. Essentially this does what I explained how to do in [part one](https://tomsbox.co.uk/2017/02/Browser-Privacy-1/) of this now 3 part article. If you're one of the billion that still wish to feed the big slurp I highly suggest you use this addon.

So that concludes this article.
