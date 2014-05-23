RT28XX-RT539X-Linux-driver
==========================

2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO updated to work with Linux kernel 3.8 and above.
Tested with Ubuntu 14.04

How to install
--------------

- sudo apt-get update
- sudo apt-get install git linux-headers-$(uname -r) build-essential dkms fakeroot
- git clone https://github.com/agerwick/RT28XX-RT539X-Linux-driver
- cd RT28XX-RT539X-Linux-driver
- sudo make
- sudo make install
- sudo nano /etc/modprobe.d/blacklist.conf
  
  Add the following lines:
  - blacklist rt2800pci
  - blacklist rt2800lib
  - blacklist rt2x00usb
  - blacklist rt2x00pci
  - blacklist rt2x00lib
  - blacklist rt2860sta
  - blacklist rt3090sta
  
  To save and exit, press Ctrl-X, Y, Enter
- sudo nano /etc/modules
  
  Add the following line:
  - rt5390sta
  
  To save and exit, press Ctrl-X, Y, Enter

Now restart the computer, or alternatively:
- sudo depmod -a
- sudo modprobe -rfv rt2800pci
- sudo modprobe -v rt5390sta

How to update the driver after a Linux kernel upgrade
-----------------------------------------------------
To update the driver (or "recompile it for your current kernel", to be exact), run the shellscript included here, named "update-driver-after-kernel-upgrade"
If you were in your home directory (that's the default when you open a terminal) when you issued the "git clone" command above, then you can enter the following code in your terminal:
- ~/RT28XX-RT539X-Linux-driver/update-driver-after-kernel-upgrade
