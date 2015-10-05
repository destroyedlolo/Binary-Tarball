# HC-913_Gentoo
Home made Gentoo/Linux images for **Klipad hc-913** (mid_a13)

This repository contains some images I made to boot my bricked Klipad HC-913 tablet on Gentoo Linux. 
My aim is to got a working *basic* system that can stick on a 1Gb SD card with some room remaining in order to get recycle this device as a dashboard for my smart home system.

## Contents

* **rootfs.xz** : naked Gentoo image with only **Directfb** and **Lua 5.1** installed from Gentoo's repository
* **script.bin** : original hardware configuration took from Android Nand
* **uEnv.txt** : additionnal kernel parameters example ; here, disabling screen blanking.
* **3.4.103+** : SunXI kernel

## Installation

## Post installation

* Change root password (Yes ! **CHANGE IT**)
* In order to avoid uneeded write access to your SDcard, add following line /etc/fstab as following (*I forgot it, oups :(*)
```
none                    /var/tmp        tmpfs           defaults        0 0
none                    /tmp            tmpfs           defaults        0 0
```
* Have you modified root password ?
* mount all or reboot
