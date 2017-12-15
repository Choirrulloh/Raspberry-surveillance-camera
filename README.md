# Raspberry-surveillance-camera

## Prerequisites
To build this project, you'll need:
* [A Raspberry Pi 3 model B](https://www.adafruit.com/product/3055) (40€)
* [A SD card](http://boutique.semageek.com/fr/773-micro-sd-16-gb-avec-adaptater-sd-et-os-noobs.html) (12€)
* [A Power Supply](http://boutique.semageek.com/fr/723-alimentation-raspberry-pi3-5v-25a-micro-usb.html) (15€)
* [A 8MP Camera V2 for Raspberry](http://boutique.semageek.com/fr/781-module-camera-8mp-v2-pour-raspberry-pi.html) (35€)
* [A 60cm Cable Camera 60](http://boutique.semageek.com/fr/365-cable-flex-610mm-pour-camera-raspberry-pi.html) (3€)
* A Wi-Fi connection
* Patience and passion
 
Total: 105€

## Raspberry Pi installation
### Install Raspbian
https://www.raspberrypi.org/documentation/installation/installing-images/

### Install PHP 7.1
https://www.noobunbox.net/serveur/auto-hebergement/installer-php-7-1-sous-debian-et-ubuntu (French link)

Check success by typing in terminal `php -v`. This should tell you the current PHP version.

### Connect and enable your camera
https://www.raspberrypi.org/documentation/configuration/camera.md

### Wi-Fi autoconnecting
`sudo nano /etc/wpa_supplicant/wpa_supplicant.conf`
Append as many networks as you want - here are a few examples:

```
# Secure Wi-Fi example:
network={
    ssid="your-ssid"
    psk="your-key"
}
```

### Fixed IP
Type in Raspberry terminal :
`sudo nano /etc/network/interfaces` then set the contents to this values at least:
```
# interfaces(5) file used by ifup(8) and ifdown(8)
# Please note that this file is written to be used with dhcpcd
# For static IP, consult /etc/dhcpcd.conf and 'man dhcpcd.conf'
# Include files from /etc/network/interfaces.d:
source-directory /etc/network/interfaces.d
auto lo
iface lo inet loopback
iface eth0 inet manual
allow-hotplug wlan0
iface wlan0 inet manual
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
allow-hotplug wlan1
iface wlan1 inet manual
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
```

Then `sudo nano /etc/dhcpcd.conf` and append this to the file:

```
# Configuration ip fix wlan :
interface wlan0
static ip_address=192.168.1.201/24 #replace 201 by your wish
static routers=192.168.1.1
static domain_name_servers=192.168.1.1
```

> [More details on this step here](http://limen-arcanum.fr/2016/03/raspberry-3-et-ip-fixe-en-wifi/) (French link)

### Check if your IP address is set well:
Reboot then check your local IP : `hostname -I`

Reboot again and re-check your local IP

If it is not same: have patience and good luck. :)


### Install VNC server on the Raspberry
To easily access to your Raspberry every time, you should install VNC. You have to install VNC server on your Raspberry and VNC viewer on you desktop. Follow this good tutorial:

https://www.raspberrypi.org/forums/viewtopic.php?t=123457

### Install VNC viewer on your desktop
https://www.realvnc.com/en/connect/download/viewer/

Launch VNC viewer and add a new connection to `192.168.1.201:1`

> Important note: be sure te be on same Wi-Fi network on both sides.


## Configuration de la camera
### Installer motion
`sudo apt-get install motion`
### Configurer motion
### Envoyer un sms en cas de detection de mouvements

## Mettre en place la visualisation du live depuis internet
### Installer un apache
### Creer une page html qui diffuse le live
### Sécuriser l'acces avec un htaccess et htpassword
### Configurer le NAT
### Tester l'acces depuis internet
