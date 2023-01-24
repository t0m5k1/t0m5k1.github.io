---
layout: post
title: Pihole in Oracle
date:   2023-01-24
description: Alternative to using Google Cloud
comments: true
toc: true
tags:
 - PC
 - Linux
 - Security
 - Privacy
---

I know there are many sites that produce these guides but I like to have my own. Additionally I also like to use unbound as a local forwarder that is configured to use root hints, This means you're not sharing more data with others and look up DNS directly.

Additonally I use the wireguard part of openVPN and only have 2 tunnels connected to my cloud: 1 my phone 2 my local DNS server.
Why do I have a local DNS server you might ask, Well it allows me to offload the actual blocking to the cloud and keeps the gui cleaner additionally it means less traffic going to the cloud so then there is less chance of hitting a fee for the compute instance


Only change configuration mentioned here, leave the rest as default.

---
# Platform Setup

Create an account with Oracle Cloud free tier: https://www.oracle.com/cloud/free

Setup a VM instance

Switch the OS from Oracle Linux to Ubuntu

Upload your own public key (this key can be generated via PuTTY)

Note down Public IP and Private IP

---
# OS Setup

Log in to Shell and switch to root: 
```
sudo su - root
```
Change root password:
```
 passwd root
```

[Note: The common practice is not to do this. Here the use case is security vs. convenience, where this approach is convenient but may be risky to permit remote access via root.]

Update the system:

```
apt-get update && apt-get upgrade -y
```
---
# Install pivpn, pihole text editor

Install and configure pivpn:
```
curl -L https://install.pivpn.io | bash
```

Select Port: `1194`

Create a default client after installation and download it [Step 25]

Install and configure Pi-Hole: 
```
curl -sSL https://install.pi-hole.net | bash
```

Select interface: `tun0`

Change the Pi-Hole password: 
```
sudo pihole -a -p
```
Install nano text editor (or your favourite alternative): 
```
sudo apt install nano -y
```
---
# Setup SSH access
Edit the SSH config file:
```
sudo nano /etc/ssh/sshd_config
```
It is upto you if you want to allow root to be able to login, Personally I do not and suffice with using sudo from a normal user.


Change following entries
```
PasswordAuthentication no > PasswordAuthentication yes

PermitRootLogin prohibit-password > PermitRootLogin yes
```

`[Note: As mentioned earlier, do this at your own risk - this method allows you to easily connect to VM and grab any file from anywhere but this may pose a security risk]`

Restart sshd: 
```
sudo systemctl restart sshd
```

---
# Setup PiVPN

Edit the server config:

```
nano /etc/openvpn/server.conf
```

Change push "dhcp-option DNS <pihole private ip goes here>"

Comment out the line which reads `push "redirect-gateway def1"` so it reads as follows:

 ```
 # push "redirect-gateway def1"
 ```

The longer the keep-alive interval the longer it will take either end of the openvpn connection to detect whether the connection is no longer alive. Because mobile devices often lose connectivity and regain it, lower values are desirable.

Comment out `keepalive 1800 3600` and add `keepalive 10 60` below it, so it appears as follows:

 ```
 # keepalive 1800 3600
 keepalive 10 60
 ```

Comment out the line which reads `cipher AES-256-CBC` and add `cipher AES-128-GCM` below it, so it reads as follows:

 ```
 # cipher AES-256-CBC
 cipher AES-128-GCM
 ```

At the bottom of the file add the following lines:

 ```
 # performance stuff
 fast-io
 compress lz4-v2
 push "compress lz4-v2"
 ```

Press `CTRL` `O` to bring up the save prompt at the bottom of Nano, press **Enter** to save. Then press `CTRL` `X` to exit

---
# Setup Oracle firewall

Search Internet on Oracle web GUI

Navigate to > Internet Gateway vcn-XXXXXXXX-XXXX 

Left column > Navigate to > Security Lists

Navigate to > Default Security List for vcn-XXXXXXXX-XXXX 

Add Ingress Rules

Source CIDR: `0.0.0.0/0`

IP Protocol: `UDP`

Destination Port Range: `1194`

Restart the VM from the Console

---
# Managing the PiVPN

set up an OpenVPN Client Profile. (You do not need to have elevated root privileges to do this.)

```
pivpn add nopass
```

Give your client profile a name. I like to use an alphanumeric string composed of the user's first name, and their device's make and model (no spaces and no special characters).

>  Make a new client profile for every device. DO NOT share a client profile between two different devices.
{: .note} 

This command will output a success message which looks like this:

   ```
   ========================================================
   Done! mypixel3xl.ovpn successfully created!
   mypixel3xl.ovpn was copied to:
     /home/myusername/ovpns
   for easy transfer. Please use this profile only on one
   device and create additional profiles for other devices.
   ========================================================
   ```

To get the **mypixel3xl.ovpn** file to your phone it is easiest to maximize your SSH window and print the file to the terminal window, to copy & paste the output:

```
cat ~/ovpns/mypixel3xl.ovpn
```

Press `CTRL` `-` until the screen zooms out to a point where you can see the entire ovpn file printed on the screen. The first line will have the word `client` and the last line is `</tls-crypt>`. Highlighting this entire chunk with a mouse will cause a scissor icon to appear in the middle of your SSH window, this means this selection has been copied to your clipboard.


---


# Moving Forwards

Suggested Block lists: I could list out all the lists I like to use but whether they're valid to you is a totally different matter. So to make it simple andd get you going I'll suggest 1 list

Configure the OISD block list, which covers almost every sub-list known to humankind: https://oisd.nl/ [follow instructions on the website and pick on need basis]

For extra configuration of other features on pihole please refer to their documentation and community.

Use following commands for periodic updates

Ubuntu: 
```
apt update && apt upgrade && apt dist-upgrade
```

Pi-Hole: 
```
pihole -up
```
Pi-Hole Gravity (adblock lists): 
```
pihole -g
```
Restart after update: 
```
reboot
```

Share this guide with whoever you like


`PLEASE NOTE i CANNOT GUARANTEE THE ABOVE GUIDE WORKS IN FULL AS THINGS CHANGE, AT THE TIME I WROTE THIS IT WORKED FOR ME`