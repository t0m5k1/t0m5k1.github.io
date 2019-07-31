---
layout: post
title: Windows Telemetry
date:   2017-02-18 11:07
description: Windows 7 – 10 Telemetry …Forced?
comments: true
toc: true
tags:
 - PC
 - Windows
 - Privacy
---


For the past few months we have seen a big change in how Microsoft decide to release major upgrades to their Windows operating system. Previously we were informed of the new release and went to a shop and purchased the media, now Microsoft has decided to follow suit with Apple and Linux distrobutions and provide digital upgrades meaning that Windows 8.1 was the last edition of Windows to be found to come on install media.
Essentially we all thought that would mean a new Windows Update control panel application or perhaps inclusion within windows App store but no Microsft were more sneaky and decided to use the normal WSUS methods and just have windows update alert you via the taskbar and install via the WSUS system.

At first this did not seem so bad and we all began to read the reviews of Windows 10 and then hide the updates if we didn’t want it. This was soon changed slightly and we also read reports of privacy brreaches in how it provides adverts and collect data, giving us all the reason why Microsoft offered Windows 10 for free even to those that had installed pirated versions of Windows.
However we then learnt that the Windows 10 upgrade was split accross multiple “hotfixes” or “patches” which basically meant it was a lot more harder to stop Windows 10 and the big clincher is that a majority of the Windows 10 hotfixes just provide the telemetry aspects of Windows 10 to Windows 7/8/8.1 and the rest of the upgrade is just contained in the larger hotfix that takes up 4.5Gb of C:\ drive space!

All of this does seem very odd and to be honest most of this has all been brushed aside by far too many people who simply state:
“So many big companies log so much of what we do online why should any of this windows 10 privacy issue bother me!”
Well essentially what Microsoft has done here is Forcibly distribute an upgrade to a mainline operating system that has a keylogger and voice recorder built into it which will effectivley turn it into a data collection source. Why you may be asking, well this is because Microsoft want to cash in on the huge market exposed by facebook who use the info you give them to sell and make money, so microsoft decided to go one better and collect data from the operating system itself!

I won’t go into a list of relevant KBs that you should uninstall and hide within windows update instead I will provide a couple of links to solutions that are updated regulary and will block, uninstall and inform you on these updates. First though here is a nice quote from the marketing head at Microsoft:

“By default Windows 10 Home is allowed to control your bandwidth usage, install any software it wants whenever it wants (without providing detailed information on what these updates do), display ads in the Start Menu (currently it has been limited to app advertisements), send your hardware details and any changes you make to Microsoft and even log your browser history and keystrokes which the Windows End User Licence Agreement (EULA) states you allow Microsoft to use for analysis.”

If that does not irk you or make you ask why then continue to use it blindly otherwise consider the alternatives:
1) get Win10 Enterprise and disable every single aspect of data collection
2) get Win10 Pro and disable only adverts being displayed
3) Learn how to stop M$ shoving Win10 down your throat and stick to Win7/8
4) get Apple and learn a new desktop
5) get Linux for free and learn a new desktop

[Batch Update Uninstaller][batch-uu]:
This will remove and hide the windows updates that provide windows telemetry (ms-spyware) To get it you just need to register with the overclockers forum, also you will want to bookmark this and update it regularly to ensure you keep all the nasty updates hidden:


Next up is [Spybot Anti-Beacon][spybot-ab]:
This is for those of you who cannot be arsed fiddling around with windows updates and updating the batch uninstaller. It is provided by the same people who make “Spybot Search and Destroy” so you be sure you are in safe hands but bear in mind that as this is a reactive peice of software nothing is removed and all it does is disable and block the telemetry:


Advice:
Considering how much M$ are positioning themselves in the information marketing business this now means all your information that is given to M$ via their telemetry effectively turns you into an ongoing source of profit for M$ even if you never update or buy their products.
The amount of information that M$ can get from your PC is currently being debated BUT legally they can obtain just as much info as what you put into your FB profile but with one large difference all the searching you do from the start/tile menu is handed over to M$ and the future of the metro interface on Windows is to integrate any app into this search facility should make you realise what M$ are trying to do.

Many of us are now disabling automatic updates on windows and having it just notifying us that there are update available rather than having them be downloaded, this is because just 3 of the telemetry updates can consume 15Gb of drive space and just as much of your bandwidth!!!!!!
The Windows 10 update alone is that size which begs the question why do it this way but M$ will just state this is their chosen delivery method but many of us do not have unlimited internet and/or don’t want to have a bloody win update consume that amount of drive space whilst it waits to be installed!

Any way I’ll leave you to it, have fun.

[batch-uu]: http://www.overclock.net/t/1572731/batch-update-uninstaller-uninstall-forced-win10-telemetry
[spybot-ab]:   https://github.com/jekyll/jekyll