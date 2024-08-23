---
layout: post
title: Current Linux Desktop
date:   2024-08-23 15:00
description: this is how I use Archlinux these days
comments: true
toc: true
tags:
 - PC
 - Linux
 - Software
 
---

So this is how it looks:

<br><img src="/assets/images/desktop-20240823.png" width="2000">

To see the original size just right click ad "Open i new tab"

This is using hyprland which is a Wayland compositor. 

The configs for the desktop and status bar can be found here:

hyprland.conf:
[https://gist.github.com/t0m5k1/fc6ee522bef837abe9237a89d6072e78][1]

binds.conf:
[https://gist.github.com/t0m5k1/6bf141cf03efb20fa1ce833369e0e1f9][2]

windowrules.conf:
[https://gist.github.com/t0m5k1/ee0f4f2c09f1ab81b1851c5b9c6bcf8c][3]

waybar config:
[https://gist.github.com/t0m5k1/6dd3984ca6a66d69fbc3cd345439e8c6][4]

waybar style.css:
[https://gist.github.com/t0m5k1/9fd15f19de038593264a1410f8d10419][5]


For this all to work you'll need to install the relevant parts and their dependencies, I use Archlinux so I'll only be providing necessary commands to get it working on there, any other distro is up to you but these configs should still function.

Run the following command: 
(NOTE: As always with Arch ensure you've already upgraded prior to installing these)
```
sudo pacman -S hyprland hyprcursor hyprutils hyprwayland-scanner xdg-desktop-portal-hyprland waybar kitty

```
Now if you find that the workspace icons are not bein displayed correctly this will be due to missing fonts, I use the nerd font version of liberation family. To get it run the following:

```
sudo pacman -S ttf-liberation-mono-nerd
```
You may also need to make some further adjustments to the waybar config to get it working as you need.
I also use for a launcher so you may need to get that too or change it to something you prefer.

```
sudo pacman -S rofi
```
Once that is installed [clone this git repo][6] and the Archlinux Icon should trigger the menu.

Hope you like this.
See ya


[1]: https://gist.github.com/t0m5k1/fc6ee522bef837abe9237a89d6072e78

[2]: https://gist.github.com/t0m5k1/6bf141cf03efb20fa1ce833369e0e1f9

[3]: https://gist.github.com/t0m5k1/ee0f4f2c09f1ab81b1851c5b9c6bcf8c

[4]: https://gist.github.com/t0m5k1/6dd3984ca6a66d69fbc3cd345439e8c6

[5]: https://gist.github.com/t0m5k1/9fd15f19de038593264a1410f8d10419

[6]: https://github.com/adi1090x/rofi
