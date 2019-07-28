---
layout: post
title: Software Recommendations
date:   2017-02-19 11:07
description: Software I trust and use.
comments: true
tags:
 - PC
 - Windows
 - Software
---


Here is a list of software I would recommend people use.
(Links either point to Major Geek or Direct to product)
Updated:
2019-07-28: I have made changes to this page to reflect my thoughts, Items that were updated will be marked as such.

## Anti Virus:

[Avira AV][Avira AV]
Many go for AVG which is good but when I used it I also heard about Avira & finally tested & it discovered 3 virus’ & a swathe of spy/adware which AVG seemingly missed during it’s 3 years worth of use. Since then I have always used it. Avira comes in many forms but the basic version is free which has real time protection, hourly updates, malware protection, rootkit protection, firewall integration, scheduled scans & many other features. Also It now has a free Android app available in google’s play store.

## Anti-Malware:

[Spybot-Search & Destroy][spybot-sd]
I use this everytime I “Clean” a Windows PC & it just works. One caveat when installing & running the “Immunization” you will have to “unlock your Hosts file” If you have done as I do & you installed Avira once SpyBot tries to access your Hosts File a pop up warning will tell you about it & so you just read that warning & click “Settings” within it & then deselect the protection for the Hosts file followed by “Apply”, keep this window open until Spybot has finished it initial scan which is well known to take at least 1 hour! Fret not as this is a sure sign that it is being thorough.

It detects and removes spyware, a relatively new kind of threat not yet covered by common anti-virus applications. Spyware silently tracks your surfing behaviour to create a marketing profile for you that is transmitted without your knowledge to the compilers and sold to advertising companies. If you see new toolbars in your Internet Explorer that you haven’t intentionally installed, if your browser crashes inexplicably, or if your home page has been “hijacked” (or changed without your knowledge), your computer is most probably infected with spyware. Even if you don’t see the symptoms, your computer may be infected, because more and more spyware is emerging. Spybot-S&D is free, so there’s no harm giving it a try to see if something has invaded your computer.

Many of you will at this point be wondering why I have not mentioned MalwareBytes and this is due to their spamvertising, also I do not like using trial versions that do not due the full job until you purchase it. Why have the ability to find issues and not fix them until you hand over cash even though you installed a free product! Sorry but there are a few alternatives that are free, will fix the issue and not spam you to purchase them

## AV+AM+WF+Firewall+VPN:

[FortiClient][fortic] (Addition)
I've used and provide support for this at work. If you have a corporate environment you administer I strongly advise you consider this along with a FortiGate Appliance.
FortiClient is more than advanced endpoint protection. As an integrated agent, FortiClient contains three key modules: Fabric Agent for security Fabric connectivity, the endpoint security modules, and the secure remote access modules. Fabric Agent shares endpoint telemetry with the Security Fabric and delivers broad endpoint visibility, compliance control, and vulnerability management. It provides advanced endpoint protection with pattern-based anti-malware, behavior-based exploit protection, web-filtering, and an application firewall. FortiClient natively integrates with FortiSandbox to detect zero-day threats and custom malware. FortiClient also provides secure remote access with built-in VPN, single-sign-on, and two-factor authentication for added security.

## Firewall:

[ZoneAlarm Free Firewall][zonealarm]
I have recently began using this purely due to the changes with both product and company, As I work in the IT industry CheckPoint is a big name to me and holds lots of trust. I have used ZoneAlarm prior to 2004 and well I think most people have uninstalled that version but now it is totally different as now it stealths all ports. Manages programs’ access to Internet and network. No longer forces toolbar, homepage changes. Resists attack. Includes identity protection, online backup.
ZoneAlarm was developed by Zone Labs, which was acquired in March 2004 by Check Point. ZoneAlarm’s firewall security products include an inbound intrusion detection system, as well as the ability to control which programs can create outbound connections. In August 2015, ZoneAlarm introduced a 100% virus-free guarantee with its Extreme Security product.

[Comodo Firewall][comodo]
I chose this due it’s simplistic layout and features given by their free edition which has also won various awards for providing a very good level of protection for a free version. So if you connect regularly to many different wireless networks on your laptop disable Windows firewall and install this asap. For Home if you are paranoid and do not trust the firewall in your own dsl router then go ahead and install this as it will not let you down.

Windows Firewall (Addition)
I'm going to mention that as it has been upgraded a lot since Windows 7 and to be fair it does a really good job, If you really don't want to add yet another piece of software then I would say forego the installation of a firewall and stick with the Windows version BUT only if you are running Windows 10 1903.


## Cleaning:

Sometimes Windows will get a bit …erm clogged up & begins to run slowly, whilst this may be a bigger technical issue it will not hurt at all to clean up a little bit.

[BleachBit][bleach] (Addition)
This is my Ccleaner replacement, It is for the advanced user and the GUI is not very freindly but make sure you take a backup first and all will be well.
When your computer is getting full, BleachBit quickly frees disk space. When your information is only your business, BleachBit guards your privacy.
Be warned though as this gem does hold power to cause problem if not used correctly!!

[CCleaner][cleaner] (Updated)
I *USED* to swear by this until they got hacked then it was an infection vector, but now they've been brought out and things are totally different.
Back in the pre-hack days if you called me out or bring your poorly injured to me you will see me use this gem of software, Seriously it solved sooooo many windows based problems for me that I take a copy of it with me where ever I go. If you download it & Install it you may also want take a look at their [guide on how to use it’s features][cc-guide].


[Defraggler][defraggler]
Do I still trust this after what was written above? ...Yes to a degree, If I need to I will use this
Whilst with windows 7, 8 and now 10 microsoft now have set their own defragmentation tool to run automatically rather than leaving it up to you to work out what it is & that it needs to be done the tool itself is still beyond basic. Defraggler is made by the people who also make ccleaner & TBH this is one of the fastest & best defragging tools there is.



Now for those of you who are more advanced & have long term Admin knowledge of Windows I have great pleasure in introducing a great script called:

[TRON][tron]
This amazing script will do pretty much everything you need to sort out either a new PC or one that needs a real good clean out.
Tron is a script that “fights for the User.” Think of it as a “tech-on-a-thumb-drive” that automates the majority of tedious work involved in disinfecting and cleaning up a Windows system.
The goal is ~85-90% automation, with the understanding some things will always be better left to the discretion of the tech. It is built with heavy reliance on community input and updated regularly.

Before you run off and download this I suggest you make sure you understand exactly what this script can do and then work out what you want it to do as with script like this it is really easy to B0rk your system! This is an advanced tool with many features all of which can be turned off

## Driver Updating:

Sometimes having to work out what drivers you need for your PC/Laptop can be a bit of a nightmare especially if you have built & customized every part of it.

[Driver Fusion AKA Driver Sweeper][dsweep]
NOTE: This program is advertising supported (Adware) and may offer to install third party programs that are not required for the program to run. These may include a toolbar, changing your homepage, default search engine or other third party programs. **Please watch the installation carefully to opt out.**

Each time I face a PC to clean & need to update the drivers I use this, it is simple, effective and get’s the job done.

Driver Fusion is the complete device and driver solution for your PC that can manage and monitor your devices and their drivers. You can install and uninstall drivers with Driver Fusion, including the ability to backup, restore and download drivers with ease. The effortless health check, including an automatic driver updater to update outdated drivers and install missing drivers, lets you scan and fix detected issues quickly. Furthermore, you can disable, enable and restart devices while Windows is running. With our cloud-powered removal engine you can delete the driver entries that are left behind by the normal uninstallers, which is especially useful when you are updating a driver or changing a device.

In addition, Driver Fusion can help you to identify devices that Windows does not recognize, generate a device and driver report, backup and restore your desktop icons and screen resolution, or read the sensor values of your devices. Driver Fusion provides you with all the information that you need to know about your devices and their drivers, allowing you to detect and solve problems or simply find your computer specifications in one place.




## Web Browser:

[Brave Browser][brave]
I used to use Chromium as I liked the web app features but Google ...you're taking the piss out of our privacy and now the whole advert eco system online is just out of control.
The suggestion to use this is based off other articles I've written on here and my experience of using it.
Along with the default install I use: Bitwarden(lastpass alternative thats FOSS), ublock origin(just in case), Duckduckgo privacy, EFF Privacy Badger. 


[Firefox][ff]
Need I say more than just give the link! lol Some people prefer not to us it but since the last update things are getting kind better that chromium, It now has it’s own market place for browser apps although many are not available for desktop use (yet)  On the whole things are a whole lot better these days & each tab creates it’s own thread which means if that tab crashes the rest of the tabs remain functional.

Chromium (Updated)
I used this browser a lot but now I relegate it due to the massive data slurp it provides Google, I removed the link too.
Chromium is what Google Chrome is built off of & due to that this is updated before google’s version but still has all the modcons of google chrome with a few added flexible bits  mainly the browser sync can be pointed at companies other than google (for those who don’t trust google!)


Internet Explorer (IE)
I would highly suggest you never use this browser UNLESS your job requires you use it, you need to access a system which will only work with IE or you design webpages in MS Front Page (because then you have to use it!) which is another app I would avidly discourage people from using. Way back when frontpage was first released microsoft had the absurd vision of “changing the internet” what that translated to was MS Word being fed waaay to many steroids & converted into a web page creator with which the resulting page had far too much useless code which was only ever used when the page was viewed with IE all other browsers ignored these tags which resulted in a very ugly webpage that looked more like a creation from kindergarten using “My First Webpage” which is basically what the geeks refer to it as. Not only it’s poor history but IE itself even today in version 10 is just a magnet for all the crudge that floats on the web, more so that there are people who create virus’ & malware targeting IE only!

Edge (New IE)
Bear in mind the latest version is based on Google-Chrome.
Whilst this is a good step in the right direction for M$ as it uses new technology and a decent backend it is still not the most secure as discovered by Trend it may have sandboxing but the implementation is somewhat lacking especially that extensions when added are not implemented in a true sandbox also it relies on a mozilla based java implementation which opens it up to the same java exploits as firefox. Development is slower than other browsers, yes updates might be tied to windows update system but a quick check of the history of these show it still is not updated as regular as other browsers. Most of the extensions people add for additional security protection (https everywhere, ublock origin, no script, lastpass) are not available although you can fudge ublock origin to work (article to come soon!) you really are just better off using a 3rd party browser like one listed above.




## Office Suite:

[Kingsoft Office Suite][kingsoft]
One thing these guy’s want to do is produce a product that resembles what it is replacing & therefore looks very similar to MS office. I can open all the latest MS files & even the layout of the buttons are in the same place so the intuitiveness of this is greatly increased by those who have had recent MS Office training. This does what MS Office can do but it is free (after 1 years it will ask you to purchase but updates are every 6-8 months so to avoid this just upgrade)

[Libre Office][libre]
I have been using this ever since Oracle purchased Open Office & I have never had an issue with it, It has the ability to do what MS office does but it tries to follow it’s own path & therefore is far less intuitive than Kingsoft. Also this is totally open source so if you are a coder & want to add an extra feature you can just grab the source & off you go 🙂

Text Editing:

[Notepad++][np++]
This has to be one the most used notepad varients & to be honest you see why when you use it, so just get it & use us it as a replacement.
Notepad++ is a text editor and source code editor for use with Microsoft Windows. Unlike Notepad, the built-in Windows text editor, it supports tabbed editing, which allows working with multiple open files in a single window.

[Atom][atom]
For those who want a bit more customisation out of their advanced editor then this will provide every function & way more.
Atom is a text editor that’s modern, approachable, yet hackable to the corea tool you can customize to do anything but also use productively without ever touching a config file

Now the chances are that some of you will disagree with my choices above but they are just that MY choices, I post this here because sometimes when I clean a PC for someone they always ask me what do I recommend, well here is what I recommend & these are based on my usage of them


[Avira AV]: http://www.majorgeeks.com/mg/get/avira_free_antivirus,1.html
[spybot-sd]: http://www.majorgeeks.com/mg/get/spybot_search_destroy_2_12_final,1.html
[fortic]: https://forticlient.com/downloads
[zonealarm]: https://www.zonealarm.com/uk/software/free-firewall/
[comodo]: http://www.comodo.com/home/internet-security/firewall.php
[bleach]: https://www.bleachbit.org/download
[cleaner]: https://www.piriform.com/ccleaner/download/standard
[cc-guide]: https://www.piriform.com/docs/ccleaner/using-ccleaner/cleaning-your-pc/cleaning-your-pc
[defraggler]: http://www.majorgeeks.com/mg/get/defraggler,1.html
[tron]: https://www.reddit.com/r/tronscript
[dsweep]: http://www.majorgeeks.com/mg/get/driver_fusion_(driver_sweeper),1.html
[brave]: https://brave.com/
[ff]: http://www.majorgeeks.com/mg/get/mozilla_firefox,1.html
[kingsoft]: http://www.ksosoft.com/downloads/office_free_2013.exe
[libre]: http://www.majorgeeks.com/mg/get/libreoffice_productivity_suite,1.html
[np++]: https://notepad-plus-plus.org/
[atom]: https://atom.io/

