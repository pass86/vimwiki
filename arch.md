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
vim /etc/pacman.d/mirrorlist
pacstrap /mnt base base-devel
genfstab -L /mnt >> /mnt/etc/fstab
cat /mnt/etc/fstab
arch-chroot /mnt
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
hwclock --systohc
```
```sh
vi /etc/locale.gen
```
```
en_US.UTF-8 UTF-8
```
```sh
locale-gen
vi /etc/hostname
```
```sh
vi /etc/locale.conf
```
```
LANG=en_US.UTF-8
```
```sh
pacman -S vim os-prober grub dialog wpa_supplicant intel-ucode
```
```sh
vim /etc/lvm/lvm.conf
```
```
use_lvmetad = 0
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
vim /etc/sudoers
```
```
%wheel ALL=(ALL) ALL
```
```sh
useradd -m -G wheel foo
passwd foo
dhcpcd
```

# network
```sh
pacman -S networkmanager network-manager-applet
systemctl disable netctl
systemctl enable NetworkManager
nm-applet
```

# desktop
```sh
pacman -S xf86-video-intel xorg sddm
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
pacman -S fcitx fcitx-im
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
