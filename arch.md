# install
```sh
wifi-menu
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
mkfs.xfs /dev/sda1
mount /dev/sda1 /mnt
vim /etc/pacman.d/mirrorlist
pacstrap /mnt base base-devel
genfstab -L /mnt >> /mnt/etc/fstab
cat /mnt/etc/fstab
arch-chroot /mnt
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
hwclock --systohc
pacman -S vim os-prober grub dialog wpa_supplicant
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

# desktop
```sh
pacman -S xf86-video-intel xorg plasma kde-applications sddm network-manager-applet
systemctl enable sddm
systemctl disable netctl
systemctl enable NetworkManager
```

# virtualbox
```sh
pacman -S virtualbox-guest-utils
```

> choose virtualbox-guest-modules-arch
