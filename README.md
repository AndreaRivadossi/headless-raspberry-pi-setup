## Headless Raspberry Pi Setup

### What You Need:
* The Raspberry Pi (rPi)
* SD or Micro SD Card (the minimum recommended card size is 8GB).
* SD or Micro SD Card reader.
* A power supply for the Raspberry Pi.

## 1. Download Raspbian Image
Download the Lite image from [here](https://www.raspberrypi.org/downloads/raspbian/).

## 2. Write The Image To The SD Card
Download and install [Win32DiskImager](https://sourceforge.net/projects/win32diskimager/), then:

* Connect the card reader or insert the SD Card in your reading support.
* Open Win32DiskImager.
* Click on `Image File` and select the Raspbian image.
* Click on `Device` and choose the drive corresponding to your Micro SD card.
* Click on `Write` and wait until the window displays “Done” under the progress bar.

In alternative you can use [Etcher](https://etcher.io), for more information read this [guide](https://www.raspberrypi.org/documentation/installation/installing-images/README.md).

## 3. Setting up wireless networking
Add a file named `wpa_supplicant.conf` in the SD boot folder, paste and edit this code:

```
country=IT
ctrl_interface=/var/run/wpa_supplicant
update_config=1

network={
    ssid="your-wifi-name"
    scan_ssid=1
    psk="your-wifi-password"
}
```

More information about this configuration file [here](https://www.raspberrypi.org/documentation/configuration/wireless/wireless-cli.md).

## 4. Enabling SSH
Add an empty file named `ssh` (without any extension) in the SD boot folder.

## 5. Boot your rPi
Insert your prepared SD card in the rPi, connect the power supply and let the magic happen

## 6.1 Find your rPi’s IP Address
If you need to access your rPi and do SSH stuff, you need to find his IP Address. Use [fing](https://www.fing.io) to have a complete list of devices connected to yout network and to discover the IP of your rPi.

## 6.2 Set up a static ip for your Raspberry Pi
Modify the file `dhcpd.conf` located in the `/etc/folder`, go to the last line and add the following content:

```
eth0 
static ip_address = 192.168.1.100 / 24 
static routers = 192.168.1.1 
static domain_name_servers = 192.168.1.1 

wlan0 interface 
static ip_address = 192.168.1.100 / 24 
static routers = 192.168.1.1 
static domain_name_servers = 192.168.1.1
```


## 7. SSH into your rPi
Use a SSH client like [PuTTY](https://www.putty.org), [Termius](https://www.termius.com) or the preinstalled terminal.

The default credentials of all rPi are:

```
username: pi
password: raspberry
```

## 8. Configure your rPi
After SSH into your rPi, you can configure it with this command:

```
sudo raspi-config
```

Now you can change your password and do other stuff. [Here](https://www.raspberrypi.org/documentation/configuration/raspi-config.md) more information about the `raspi-config`.