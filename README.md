# UbuntuServerRice
Quick script to install some rice on Ubuntu Server


## Update system
1. Type sudo apt update
2. Type sudo apt upgrade
3. Type y to confirm upgrades and hit enter

## Nvidia Drivers
* Type sudo apt install nvidia-driver-470

## Add i3wm Stable Repo
Following the guide at https://i3wm.org/docs/repositories.html
Not installing at the end
* /usr/lib/apt/apt-helper download-file https://debian.sur5r.net/i3/pool/main/s/sur5r-keyring/sur5r-keyring_2023.02.18_all.deb keyring.deb SHA256:a511ac5f10cd811f8a4ca44d665f2fa1add7a9f09bef238cdfad8461f5239cc4
*  sudo apt install ./keyring.deb
* echo "deb http://debian.sur5r.net/i3/ $(grep '^DISTRIB_CODENAME=' /etc/lsb-release | cut -f2 -d=) universe" | sudo tee /etc/apt/sources.list.d/sur5r-i3.list
* sudo apt update

## Install xorg xinit
* sudo apt install xorg xinit
* type y and hit enter to accept

## Install i3 and dependencies
* sudo apt install i3 i3lock i3status i3blocks dmenu terminator firefox
* type y and hit enter to accept

## Copy xinitrc to home directory
* sudo cp /etc/X11/xinit/xinitrc ~/.xinitrc

## Edit .xinitrc
* sudo vim .xinitrc
* add exec i3 to the final line

## Edit .profile in home directory to startx automatically
* #Startx Automatically
* if [[ -z "$DISPLAY" ]] && [[ $(tty) = /dev/tty1 ]]; then
*  . startx
*  logout
* fi
