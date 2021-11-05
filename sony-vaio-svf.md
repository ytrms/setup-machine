- [General](#general)
  - [Install gh to make GitHub authentication easier](#install-gh-to-make-github-authentication-easier)
- [Ubuntu 20.04](#ubuntu-2004)
  - [Installing Ubuntu](#installing-ubuntu)
    - [From Debian-based distros](#from-debian-based-distros)
  - [Fix keyboard not working after opening the lid](#fix-keyboard-not-working-after-opening-the-lid)
  - [Telegram and VSCode](#telegram-and-vscode)
  - [Fix bitmap fonts not working](#fix-bitmap-fonts-not-working)
- [Fedora 35](#fedora-35)
  - [Keyboard not working](#keyboard-not-working)
  - [Wi-Fi not working](#wi-fi-not-working)

# General
## Install gh to make GitHub authentication easier
- ```curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo gpg --dearmor -o /usr/share/keyrings/githubcli-archive-keyring.gpg```
- ```echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null```
- ```sudo apt update```
- ```sudo apt install gh```
- ```gh auth login```

# Ubuntu 20.04
## Installing Ubuntu
### From Debian-based distros
- ```sudo apt install usb-creator-gtk```

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

## Telegram and VSCode
Install from snap. ```snap install code --classic``` and ```snap install telegram-desktop```.

## Fix bitmap fonts not working
- ```rm /etc/fonts/conf.d/70-no-bitmaps.conf```
- ```ln -s ../conf.avail/70-force-bitmaps.conf /etc/fonts/conf.d/```
- ```dpkg-reconfigure fontconfig-config```
- ```dpkg-reconfigure fontconfig```

Note: only bitmap fonts in the .otb format work. Don't even try with others.

# Fedora 35
## Keyboard not working
See above

## Wi-Fi not working
On Ubuntu, If you check the "Third-party drivers" option while installing, you should be good. If you don't, plug via ethernet and install bcmwl-kernel-source. Or open "Additional Drivers" and you should be able to install them from there.

