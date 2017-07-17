# ssh key
* local
    * cd ~
    * mkdir .ssh
    * cd .ssh
    * ssh-keygen -t rsa -b 4096 -C "foo@gmail.com"
    * scp id_rsa.pub foo@nas.lan:/home/foo
    * vi config
        * Host nas
        *     HostName nas.lan
        *     User foo
    * chmod 600 config
    * chmod 600 id_rsa
* remote
    * cd ~
    * mkdir .ssh
    * cat id_rsa.pub >> .ssh/authorized_keys
    * rm id_rsa.pub
    * sudo vi /etc/ssh/sshd_config
        * StrictModes no
        * RSAAuthentication yes
        * PubkeyAuthentication yes
    * sudo systemctl restart sshd

# root login
* sudo vi /etc/ssh/sshd_config
* PermitRootLogin no

# firewalld
* systemctl start firewalld
* systemctl stop firewalld
* systemctl enable firewalld
* systemctl disable firewalld
* firewall-cmd --state

# disable selinux
* sudo vi /etc/sysconfig/selinux
    * SELINUX=disabled
* sestatus

# hostname
* sudo hostnamectl set-hostname vps

# mount new drive
* parted
    * sudo parted -l
    * sudo parted /dev/sdb
        * mklabel gpt
        * mkpart primary 2048s 100%
        * print
        * quit
    * sudo mkfs.xfs -f /dev/sdb
    * sudo vi /etc/fstab
        * /dev/sdb /mnt/hdd3 xfs defaults 0 0
    * sudo reboot
* fdisk
    * sudo fdisk -l
    * sudo fdisk /dev/sdb
        * press n<enter>
        * press p<enter>
        * press <enter>
        * press <enter>
        * press <enter>
        * press t<enter>
        * press 8e<enter>
        * press w<enter>

# lvm create
* sudo parted /dev/sdb
    * ...
    * toggle 1 lvm
    * ...
* sudo parted /dev/sdc
    * ...
    * toggle 1 lvm
    * ...
* sudo parted -l
* sudo pvcreate /dev/sdb1 /dev/sdc1
* sudo pvs
* sudo pvscan
* sudo pvdisplay
* sudo vgcreate -s 1024M volume /dev/sdb1 /dev/sdc1
* sudo vgs
* sudo vgscan
* sudo vgdisplay
* sudo lvcreate --name data --size 7T volume
* sudo lvs
* sudo lvscan
* sudo lvdisplay
* sudo mkfs.xfs /dev/volume/data
* sudo mkdir /data
* sudo mount /dev/volume/data /data
* df -h
* sudo vi /etc/fstab
    * /dev/mapper/volume-data /data xfs defaults 0 0
* sudo reboot

# volume group extend
* sudo parted /dev/sdd
    * ...
    * toggle 1 lvm
    * ...
* sudo parted -l
* sudo pvcreate /dev/sdd1
* sudo pvs
* sudo pvscan
* sudo pvdisplay
* sudo vgextend volume /dev/sdd1
* sudo vgs
* sudo vgscan
* sudo vgdisplay

# logical volume extend
* sudo lvextend -l +100%FREE /dev/volume/data
* sudo xfs_growfs /dev/volume/data
* df -h

# add sudo user
* usermod -aG wheel foo

# group
* /etc/group

# passwd
* /etc/passwd

# change ownership
* sudo chown -R foo:foo path

# delete old linux kernel
* sudo yum install yum-utils
* sudo package-cleanup --oldkernels --count=2
* sudo vi /etc/yum.conf
    * installonly_limit=2

# kernel version
* uname -a

# centos version
* cat /etc/redhat-release

# md5
* md5sum foo

# smartctl
* sudo yum install smartmontools
* sudo smartctl -i /dev/sda
* sudo smartctl -s on /dev/sda
* sudo smartctl -a /dev/sda

# virtual console
* ctrl + alt + f2