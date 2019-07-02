---
layout: post
title: Communicate Like a Secret Agent
categories: [Privacy]
---

Increase privacy with anonymous, offline chat and file sharing.

If you are concerned about privacy and the risk of spying, you can reduce this risk by using something called a PirateBox for discrete communication. A PirateBox is used to create both a Wi-Fi network and file server that allows nearby people to connect and communicate without having those communications touch the internet. This private, local network gives users the ability to chat and share files while never touching an online network. Data is privately routed through the device avoiding cellular and standard communications that go over the internet. 

By leveraging the wireless card of a Raspberry Pi we can bridge the restrictions that would normally be used such as cables and having to rely on third-party infrastructure or hardware. This provides us with a portable Wi-Fi hotspot that can easily be concealed.

We will be using a Raspberry Pi Zero W for this guide, but you can use a Raspberry Pi 3 or another model with a wireless adapter.

Download the correct PirateBox image for the Raspberry Pi hardware you are using.

Once the download is complete, flash the image to the micro SD card.

## Get Started
Load the micro SD card into the Raspberry Pi and boot up. After a few minutes, browse Wi-Fi access points around you and look for one name `PirateBox - Share Freely`.

Using a network scanning service like Nmap or Fing we can find the IP address of the Raspberry Pi.

The PirateBox is configured with default credentials for logging in. Both the user and password are `alarm`.

SSH into the PirateBox as the user `alarm` using the IP address recently discovered.
```shell
ssh alarm@<IP ADDRESS>
```

Once you have a successfull SSH connection you will be prompted to enter in a password. Let's go ahead and change the password using the `passwd` command.

In the network scan we can see http service running on port 80. Enter the Raspberry Pi's IP address into the browser URL and hit <kbd>Enter</kbd>. This should bring up the running PirateBox server. Our PirateBox is now available for further configuration. 

## Configure the PirateBox

### Enable Timesave

### Enable Discussion Board
A forum can help segment discussions for organized communication over specific topics.

### USB Storage
Unless you are using a micro SD card with a large storage capacity you'll most likely want to leverage a USB thumb drive or external hard drive.

### Best Practices
Safely shutdown the PirateBox with
```shell
sudo shutdown -h now
```

## PirateBox Mods

### Enable Persistent Chat
By default chat, known as Shoutbox, is reset on startup. To disable this edit the file **/opt/piratebox/conf/piratebox.conf** and set the following to **no**.
```shell
# Reset Shoutbox on Startup?
RESET_CHAT="yes"
```

### Enable Wiresless Protected Access
To restrict access to your private box edit the file **/opt/piratebox/conf/hostapd.conf** to set a password for WPA
```shell

```

### Rename SSID
Edit the file **/opt/piratebox/conf/hostapd.conf** and change the line
```shell
ssid=PirateBox - Share Freely
```

### Change Hostname

```shell

```

### Change IP Address
Edit the file **/opt/piratebox/conf/piratebox.conf** and change the line
```shell
#Network
NET=192.168.77
```

More modifications can be found on the offical PirateBox website [here](https://piratebox.cc/raspberry_pi:mods).
