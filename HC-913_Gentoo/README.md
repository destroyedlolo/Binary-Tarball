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
Providing your SDCart is mounted as **/dev/sdb**

(**Caution : ALL DATA WILL BE ERASED**)
### Boot
```
cd 3.4.103+/bootloader/
dd if=u-boot-sunxi-with-spl.bin of=/dev/sdb bs=1024 seek=8
```
### Partition your card
```
cat <<EOT | sfdisk --in-order -L -uM /dev/sdb
> 1,16,c
> ,,L
> EOT

mkfs.vfat /dev/sdb1
mkfs.ext4 /dev/sdb2
```
Note : sdb1 may be an ext2 partition as well.

### Feed boot partition
In **sdb1** copy :
* **script.bin**
* **uEnv.txt** and customize it if needed (you may remove this file if you don't have to add custom options)
* **3.4.103+/uImage**

### Feed root partition
* extract **rootfs.tar.xz** in **/dev/sdb2**
* in newly created **lib/modules/**, extract **3.4.103+/modules.tar.xz**

### boot
Unmount your sdcard, put it on your tablet and ... boot.

## Post installation

* Change root password (Yes ! **CHANGE IT**) : the defaut one is *root*
* In order to avoid uneeded write access to your SDcard, add following line /etc/fstab as following (*I forgot it, oups :(*)
```
none                    /var/tmp        tmpfs           defaults        0 0
none                    /tmp            tmpfs           defaults        0 0
```
* Have you modified root password ?
* mount all or reboot
