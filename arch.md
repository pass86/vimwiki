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
press p<enter>
press w<enter>
```
```sh
mkfs.xfs /dev/sda1
mount /dev/sda1 /mnt
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
grub-install --target=i386-pc /dev/sda
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
```
