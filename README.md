# RaspberryPiZeroW-Wireless-Cli
This repository contains all it needs to prepare a Raspberry Pi Zero W so that it can be accessed via SSH over Wifi without a screen.

**The following instructions are for Raspberry Pi OS Buster versions only. 
Config files from older versions are different.**

1. Get the latest Raspberry Pi OS (previously called Raspbian) image: [raspberrypi.org](https://www.raspberrypi.org/downloads/raspberry-pi-os/) 
2. Get [Etcher.io](https://etcher.io) to format the SD card and flash the Raspberry Pi OS image onto it
3. Install Etcher and flash the image to the SD card.
4. Remove and reinsert the SD card. You should now see the partition labeled with 'boot'
5. On the root of the partition 'boot', create a file named shh (e.g. Terminal: 'touch ssh')
6. Create another file 'wpa_supplicant.conf' (e.g. Terminal: 'touch wpa_supplicant.conf')
7. With the use of your preferred texteditor (e.g. nano), edit the file 'wpa_supplicant.conf' as described below:

```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
country=DE
update_config=1

network={
    ssid="Name of the WiFi Network"
    psk="Password of the WiFi Network"
    key_mgmt=WPA-PSK
}
```

Edit: 
- country=YOUR_ISO_COUNTRY_CODE -- can be found on [Wikipedia](https://en.wikipedia.org/wiki/ISO_3166-1)
- ssid=
- psk

Save the file.

8. Eject the SD card, put it in the Pi and boot the device. Your Raspberry Pi Zero W should now connect to your WiFi with SSH enabled to connect to.
