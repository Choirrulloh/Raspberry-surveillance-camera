# Raspberry-surveillance-camera

## Prerequisites
To build this project, you'll need:
* [A Raspberry Pi 3 model B](https://www.adafruit.com/product/3055) (40€)
* [A SD card](http://boutique.semageek.com/fr/773-micro-sd-16-gb-avec-adaptater-sd-et-os-noobs.html) (12€)
* [A Power Supply](https://www.amazon.fr/SainSmart-Certified-Raspberry-Adaptateur-Certification/dp/B01LHE8DBU/ref=sr_1_cc_2?s=aps&ie=UTF8&qid=1513517344&sr=1-2-catcorr&keywords=raspberry+3+Power+supply) (8€)
* [A 8MP Camera V2 infrarouge for Raspberry](https://www.kubii.fr/fr/idees-cadeaux/1654-nouvelle-camera-infrarouge-v2-8mp-640522710898.html) (35€)
* [A 60cm Cable Camera 60](http://boutique.semageek.com/fr/365-cable-flex-610mm-pour-camera-raspberry-pi.html) (3€)
* [A camera support](https://www.kubii.fr/fr/boitiers-raspberry-pi/801-boitier-camera-raspberry-pi-3272496002487.html?search_query=2334485&results=1) (9€)
* [A Raspberry case + heat sink](https://www.amazon.fr/gp/product/B01CPCMWWO/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1) (7€)
* [A fake camera](https://www.amazon.fr/gp/product/B012S908H0/ref=oh_aui_detailpage_o03_s00?ie=UTF8&psc=1) (27€)
* A Wi-Fi connection
* Patience and passion

Total: 141€

## Hardware
Connect you camera on your raspberry

Connect your Raspberry to internet with an ethernet link. It is required for the MotionEyeOS install but you will can removed it just after installation and use wifi connect.

## Install MotionEyeOS
Download MotionEyeOS : https://github.com/ccrisan/motioneyeos/releases

Install MotionEyeOS : https://github.com/ccrisan/motioneyeos/wiki/Installation

Get your Raspberry local IP by looking along informations displayed on the Raspberry screen.

## Configure MotionEyeOS
With a computer connected on the same network with your Raspberry, open a browser and type your raspberry local IP (for me `http://192.168.1.111`).

Login with `admin` and no password.
[![admin password](https://i.imgur.com/sx35FB1.jpg)](https://i.imgur.com/sx35FB1.jpg)

You can see the live video of your camera.
[![You can seen the live video of your camera](https://i.imgur.com/wUQCzEi.jpg)](https://i.imgur.com/wUQCzEi.jpg)

Go to `Settings` on top left, then `General settings` and define your `Admin Password` and your `Surveillance Password`. If you don't define your `Surveillance Password`, your live video will be public accessible on internet.
[![Login with admin and no password](https://i.imgur.com/AzRLWMM.jpg)](https://i.imgur.com/AzRLWMM.jpg)

Then in `Network` define your static wifi IP.
[![Set your static wifi connection](https://i.imgur.com/kcWYRFa.jpg)](https://i.imgur.com/kcWYRFa.jpg)

`Apply` these modifications.

Unlink the ethernet link. Now your Raspberry will use your wifi network.

Check to access to your Raspberry by typing the wifi local IP in browser on an other device connected to the same wifi network.

And then explore all options and defined it as you wish.

This is my configuration :

[![Video](https://i.imgur.com/jfi8q6y.jpg)](https://i.imgur.com/jfi8q6y.jpg)
[![Motion](https://i.imgur.com/CrFGWuo.jpg)](https://i.imgur.com/CrFGWuo.jpg)


> Check your Rasbperry local access by typing your Raspberry local IP (`192.168.1.202`) in a browser on a device connected on same wifi network.


## Configure the access to your Raspberry from Internet

My modem is a Huawei E5180s-22 but your modem can be different, the forwarding (NAT) configuration will be similar.

[![Huawei E5180s-22](http://www.journaldugeek.com/wp-content/blogs.dir/1/files/2017/01/bouygues-4G-box-04.jpg)](http://www.journaldugeek.com/wp-content/blogs.dir/1/files/2017/01/bouygues-4G-box-04.jpg)

Go to your modem admin panel control and add a forwarding (NAT) to your Raspberry local IP :

[![NAT](https://i.imgur.com/dAyRUhN.jpg)](https://i.imgur.com/dAyRUhN.jpg)

> Check your Rasbperry public access : type your modem public IP in a browser, you should access successfully to your Raspberry.


## Configure a human friendly domain with www.noip.com to access to your Raspberry from Internet

### Create an account on www.noip.com

Go to on https://www.noip.com/.

Create a free account.

Create a `host`.

[![noip](https://i.imgur.com/maHyJ2l.jpg)](https://i.imgur.com/maHyJ2l.jpg)

This host is a human friendly address (e.i. `www.maisonlimoges.ddns.net`) which will redirect to your modem public IP.

### Install the noip client on a device connected on same wifi network

#### Windows

Download the client https://www.noip.com/download?page=win and install it on your windows computer using the same Raspberry network wifi.

[![client](https://i.imgur.com/6qSw5hg.jpg)](https://i.imgur.com/6qSw5hg.jpg)

#### Raspbian

Follow this good tutorial : http://fr.sizious.com/2017/04/30/comment-installer-no-ip-dynamic-update-client-duc-sous-raspbian/

> Check your Rasbperry public access with a human friendly domain by typing it in a browser.

## Use your own domain to access to your Raspberry

Create on your ftp server a `.htaccess` file with :
```
redirect 301 /camera http://maisonlimoges.ddns.net
```

Now you can access to your camera every where with your own domain :).

Enjoy