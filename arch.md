# install
```sh
wifi-menu
timedatectl set-ntp true
fdisk -l
```
```sh
fdisk /dev/sda
```
o<enter>
n<enter>
<enter>
<enter>
<enter>
p<enter>
w<enter>
```sh
mkfs.xfs /dev/sda1
mount /dev/sda1 /mnt
pacstrap /mnt base base-devel
genfstab -L /mnt >> /mnt/etc/fstab
cat /mnt/etc/fstab
arch-chroot /mnt
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
hwclock --systohc
pacman -S vim os-prober grub
```
```sh
vim /etc/lvm/lvm.conf
```
use_lvmetad = 0
```sh
grub-install --target=i386-pc /dev/sda
vim /boot/grub/grub.cfg
reboot
```
