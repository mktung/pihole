# PiHole Manual

## What is a PiHole?
A PiHole is a network level adblocker and tracker blocker, a “black hole” (DNS sinkhole) that can run on microcontrollers like the Raspberry Pi. The model I specifically installed on is a Raspberry Pi Zero W. It protects you in mobile apps that browser extensions can’t reach and speeds up connection time by preventing the ad requests from reaching your device.

## How do I use it?
I’ve installed all the software on the microcontroller and fitted it with a case, so all you need to do is plug it in and **use the device as the router’s DNS server**. After that, you should never have to touch it again. The included power cable should fit in one of the device’s two micro-usb ports.

## How do I set the DNS server?
Log into the router settings and go to the DHCP/DNS settings page. From here, changing the LAN settings so that the router accepts a single static DNS: `192.168.1.200` (the static IP I’ve set to the PiHole). By default, you’ll likely have two DNS servers; something similar to `8.8.8.8` - this is what you want to change. Ensure you’re changing the LAN settings and not the WAN settings.

## How do I maintain the device?
To access the device, you can `ssh` into the server. On Windows, open the command prompt and type in 
```
ssh pi@192.168.1.200
```
This command logs you in to the server at `192.168.1.200` with the user `pi`. If you successfully connect, the server should prompt you to enter the account's password, which I've set to the old wi-fi password for now. From here, you can run anything on the server's command line. Run these three in order to update your software:
```
sudo apt-get update
sudo apt-get upgrade
pihole -up
``` 
**Before unplugging the server, you should prevent SD card corruption by running:**
```
sudo shutdown now
``` 
While this is technically good practice, you don't have to do anything described in this section and it should work just fine.

## What's this junk in the bag?
Those are other accessories that came with the Raspberry Pi kit, which will be useful if you ever need to debug the device. While you should be able to `ssh` into the server, having physical access is useful. It should include:
- MiniHDMI to HDMI cable so you can plug it into a screen
- MiniUSB to USB Hub so you can plug in a keyboard or other
- MicroSD card to SD converter so you can directly manipulate the drive
- Extra case parts if something goes wrong
- Ribbon cable if you want to repurpose the device

## If you want to customize the device
If you want to get into the gritty details of the PiHole, the main settings can be configured through `sudo raspi-config` on the command line. All other commands are standard Linux, particularly borrowed from Debian. Most importantly, the PiHole command allows you to manage a wide array of options, which are available [here](https://docs.pi-hole.net/core/pihole-command/). If you ever need help with something, feel free to text/call me.

Merry Christmas Dad!
