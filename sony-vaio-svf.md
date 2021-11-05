- [General](#general)
- [Ubuntu 20.04](#ubuntu-2004)
  - [Fix keyboard not working after opening the lid](#fix-keyboard-not-working-after-opening-the-lid)
- [Fedora 35](#fedora-35)
  - [Keyboard not working](#keyboard-not-working)
  - [Wi-Fi not working](#wi-fi-not-working)

# General
The device's wireless adapter's drivers are proprietary.

Wireless adapter: ```Broadcom BCM43142 802.11b.g/n```

# Ubuntu 20.04
Wi-Fi should work if you install with ethernet attached, but if it doesn't, ```sudo apt install bcmwl-kernel-source```.

## Fix keyboard not working after opening the lid
- ```sudo nano /etc/default/grub```
- append ```GRUB_CMDLINE_LINUX_DEFAULT="i8042.direct i8042.dumbkbd"``` to the file
- ```sudo update-grub```
- Restart the machine

This fixes the keyboard but breaks the caps/num lock indicator lights. Lorenzo from the future: trust me, I tried everything. The only way to somewhat get that back is by installing [this GNOME extension](https://extensions.gnome.org/extension/36/lock-keys/) which adds those indicators to the top bar.

Then you discover that with the latest versions of Firefox, you can't install GNOME extensions anymore from the browser. So install it this way:

- From the extension page, select the version of GNOME you're running (```gnome-extensions --version```) then select the latest version of the extension.
- Extract the zip
- Open ```metadata.json``` that's in the zip
- Copy the value at ```UUID```
- Rename the folder where you've extracted the files to the value of ```UUID```
- Move the folder to ```/Users/lorenzo/.local/share/gnome-shell/extensions/``` (create it if it doesn't exist)
- Reboot for good measure
- Install GNOME Tweak Tools ```sudo apt install gnome-tweak-tools```
- Open the tweak tools. the extension will be there.

# Fedora 35
## Keyboard not working
See above

## Wi-Fi and Bluetooth not working
- ```sudo dnf -y install https://github.com/UnitedRPMs/unitedrpms/releases/download/19/unitedrpms-$(rpm -E %fedora)-19.fc$(rpm -E %fedora).noarch.rpm```
- ```sudo dnf install broadcom-wl-dkms broadcom-bt-firmware```

The system will see wireless connections around you but when you try to connect, it'll say it can't. Turn off your "wired" connection and it'll work. I don't know why this works.

If that for some reason stops working, welcome to painville.

Try this:
https://forums.fedoraforum.org/showthread.php?325107-HELP-Broadcom-wifi-(BCM43142)-not-working-in-Fedora-33-WS

If that doesn't work, try this:
https://forums.fedoraforum.org/showthread.php?303933-broadcom-wl-installed-but-wl-not-found&s=dbe3b6715167ab93894ff7d4c16dd543&p=1790476#post1790476


