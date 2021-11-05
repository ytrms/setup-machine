Just trying to save myself some headaches in the future.

For device-specific problems, check the other files in this repo ([Sony Vaio SVF](sony-vaio-svf.md)) for example.

- [General](#general)
  - [Install gh to make GitHub authentication easier](#install-gh-to-make-github-authentication-easier)
  - [Is there a good, working, and supported way to mount Google Drive as a volume on GNU/linux distros?](#is-there-a-good-working-and-supported-way-to-mount-google-drive-as-a-volume-on-gnulinux-distros)
  - [Automatically switch between light and dark mode on GNOME](#automatically-switch-between-light-and-dark-mode-on-gnome)
- [Ubuntu 20.04](#ubuntu-2004)
  - [Installing Ubuntu](#installing-ubuntu)
    - [From Debian-based distros](#from-debian-based-distros)
    - [From anywhere else](#from-anywhere-else)
  - [Installing Telegram and VSCode](#installing-telegram-and-vscode)
  - [Fix bitmap fonts not working](#fix-bitmap-fonts-not-working)
- [Fedora 35](#fedora-35)
  - [Installing Fedora](#installing-fedora)
    - [From Debian-based distros](#from-debian-based-distros-1)
    - [From anywhere else](#from-anywhere-else-1)

# General
## Install gh to make GitHub authentication easier
- ```sudo apt install curl```
- ```curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo gpg --dearmor -o /usr/share/keyrings/githubcli-archive-keyring.gpg```
- ```echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null```
- ```sudo apt update```
- ```sudo apt install gh```
- ```gh auth login```

## Is there a good, working, and supported way to mount Google Drive as a volume on GNU/linux distros?
No. ```google-drive-ocamlfuse``` is the best we've got so far. Guide to install it [here](https://www.xmodulo.com/mount-google-drive-linux.html).

## Automatically switch between light and dark mode on GNOME
- https://extensions.gnome.org/extension/2236/night-theme-switcher/

To install, follow the steps in [sony-vaio-svf.md](sony-vaio-svf.md).

# Ubuntu 20.04
## Installing Ubuntu
### From Debian-based distros
- ```sudo apt install usb-creator-gtk```

### From anywhere else
uNetBootin

## Installing Telegram and VSCode
Install from snap. ```snap install code --classic``` and ```snap install telegram-desktop```.

## Fix bitmap fonts not working
- ```rm /etc/fonts/conf.d/70-no-bitmaps.conf```
- ```ln -s ../conf.avail/70-force-bitmaps.conf /etc/fonts/conf.d/```
- ```dpkg-reconfigure fontconfig-config```
- ```dpkg-reconfigure fontconfig```

Note: only bitmap fonts in the .otb format work. Don't even try with others.

# Fedora 35
## Installing Fedora
### From Debian-based distros
- ```sudo apt install flatpak```
- ```flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo```
- ```flatpak install mediawriter```
### From anywhere else
- [getfedora.org]()