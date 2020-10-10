# install
```sh
wifi-menu
dhcpcd
timedatectl set-ntp true
fdisk -l
```
```sh
fdisk /dev/sda
```
```
press o<enter>
press n<enter>
press <enter>
press <enter>
press <enter>
press <enter>
press p<enter>
press w<enter>
```
```sh
mkfs.ext4 /dev/sda1
mount /dev/sda1 /mnt
# Move up 163
vim /etc/pacman.d/mirrorlist
pacstrap /mnt base linux linux-firmware base-devel
genfstab -U /mnt >> /mnt/etc/fstab
cat /mnt/etc/fstab
arch-chroot /mnt
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
hwclock --systohc
pacman -S vim
```
```sh
# Uncomment en_US.UTF-8 UTF-8
vim /etc/locale.gen
locale-gen
```
```sh
# Add myhostname
vim /etc/hostname
```
```sh
# Add LANG=en_US.UTF-8
vim /etc/locale.conf
```
```sh
vim /etc/hosts
```
```
127.0.0.1 localhost
::1 localhost
127.0.1.1 myhostname.localdomain myhostname
```
```sh
pacman -S grub intel-ucode
```
```sh
grub-install /dev/sda
grub-mkconfig -o /boot/grub/grub.cfg
vim /boot/grub/grub.cfg
passwd
exit
reboot
```
```sh
# Uncomment %wheel ALL=(ALL) ALL
vim /etc/sudoers
```
```sh
useradd -m -G wheel user00
passwd user00
```

# fix "Re-reading the partition table failed device or resource busy"
* reboot

# network use systemd-networkd
```
sudo vim /etc/systemd/network/20-wired.network
```
```
[Match]
Name=en*

[Network]
DHCP=yes
```
```
sudo systemctl enable systemd-networkd
sudo systemctl start systemd-networkd
sudo networkctl status

```

# network use NetworkManager
```sh
pacman -S networkmanager iw wpa_supplicant
systemctl disable netctl
systemctl enable NetworkManager
nmtui
```

# btrfs
```sh
pacman -S btrfs-progs
```

# desktop
```sh
pacman -S xf86-video-intel xorg sddm compton network-manager-applet
systemctl enable sddm
```

# awesome
```sh
pacman -S awesome terminator
mkdir -p ~/.config/awesome
cp /etc/xdg/awesome/rc.lua ~/.config/awesome
```

# chromium
```sh
pacman -S chromium
```

# fonts
```sh
pacman -S adobe-source-han-sans-cn-fonts adobe-source-code-pro-fonts
```

# ssh-keygen
```sh
pacman -S openssh
```

# virtualbox
```sh
pacman -S virtualbox-guest-utils
```
```
choose virtualbox-guest-modules-arch
```

# installed package
```sh
pacman -Qqe
```

# package files
```sh
pacman -Ql foo
```

# aur package
* Dowload snapshot
```sh
makepkg -si
```

# caps to ctrl
```sh
vim .bashrc
setxkbmap -option ctrl:nocaps
```

# input method
```sh
pacman -S fcitx fcitx-im fcitx-configtool
```
* fcitx-sogoupinyin

# sound card
```sh
/etc/modprobe.d/alsa-base.conf
```
```
options snd_hda_intel index=1,0
```
```sh
pacman -S alsa-utils
amixer sset Master unmute
amixer set Master 60%
```

# boot log
```sh
dmsg
```

# core dump
```
/var/lib/systemd/coredump
```

# update package
```sh
pacman -Syu
```

# caps to ctrl
```sh
vim /usr/local/share/kbd/keymaps/personal.map
```
```sh
keymaps 0-127
keycode 58 = Control
```
test
```sh
loadkeys /usr/local/share/kbd/keymaps/personal.map
```
load at boot
```sh
vim /etc/vconsole.conf
```
```sh
KEYMAP=/usr/local/share/kbd/keymaps/personal.map
```

# lid
```sh
# Set HandleLidSwitchExternalPower=ignore
vim /etc/systemd/logind.conf
```

# battery
```sh
pacman -S acpi
acpi
```
