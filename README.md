RT28XX-RT539X-Linux-driver
==========================

2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO updated to work with Linux kernel 3.8 and above.
Tested with Ubuntu 14.04

How to install
==============

sudo apt-get update
sudo apt-get install git linux-headers-$(uname -r) build-essential dkms fakeroot
git clone https://github.com/agerwick/RT28XX-RT539X-Linux-driver
cd RT28XX-RT539X-Linux-driver
sudo make
sudo make install

sudo nano /etc/modprobe.d/blacklist.conf
# add the following lines:
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2860sta
blacklist rt3090sta
# To save and exit, press Ctrl-X, Y, Enter

sudo nano /etc/modules
# add the following line:
rt5390sta
# To save and exit, press Ctrl-X, Y, Enter

# restart the computer, or alternatively:
sudo depmod -a
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt5390sta
