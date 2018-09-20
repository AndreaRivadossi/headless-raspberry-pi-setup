## Headless Raspberry Pi Setup

### What You Need:
* The Raspberry Pi :P
* SD or Micro SD Card (the minimum recommended card size is 8GB).
* SD or Micro SD Card reader.
* A power supply for the Raspberry Pi.

## 1. Download Raspbian Image
Download the Lite image from [here](https://www.raspberrypi.org/downloads/raspbian/).

## 2. Write The Image To The SD Card
Download and install [Win32DiskImager](https://sourceforge.net/projects/win32diskimager/), then:

* Open Win32DiskImager.
* Click on `Image File` and select the Raspberry image.
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

## Enabling SSH
Add an empty file named `ssh` (without any extension) in the SD boot folder.

## Boot your Pi

## Find your Pi’s IP Address

## SSH into your Pi

## Configure your Pi

## Set up a static ip for your Raspberry Pi (optional)