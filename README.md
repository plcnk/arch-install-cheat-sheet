# Arch Linux Installation Cheat Sheet

## Install System

* `loadkeys fr-latin1`
* Try to ping something
* `timedatectl set-ntp true`
* `wipefs -a /dev/sda` (Replace sda with whatever disk label you have)
* `fdisk /dev/sda`
  * Boot partition
    * Primary --> Partition 1 --> +512M
    * Switch bootable flag (a)
  * Swap partition
    * Primary --> Partition 2 --> +1G
    * Partition type (t) 82 (Swap)
  * Root partition
    * Primary --> Partition 3 --> Rest of the disk
* `mkfs.ext4 /dev/sda1`
* `mkswap /dev/sda2`
* `mkfs.ext4 /dev/sda3`
* `mount /dev/sda3 /mnt`
* `mkdir /mnt/boot`
* `mount /dev/sda1 /mnt/boot`
* `swapon /dev/sda2`
* `pacstrap /mnt base base-devel linux linux-firmware vim`
* `genfstab -U /mnt >> /mnt/etc/fstab` (Generate with UUIDs, safer)
* `arch-chroot /mnt /bin/bash`
* `pacman -S networkmanager grub`
* `systemctl enable NetworkManager`
* `grub-install /dev/sda`
* `grub-mkconfig -o /boot/grub/grub.cfg`
* `passwd`
  * Type and confirm root password
* `ln -sf /usr/share/zoneinfo/Europe/Paris /etc/localtime`
* `hwclock --systohc`
* `vim /etc/locale.gen`
  * Search for locale (en_US), uncomment and save
* `locale-gen`
* `vim /etc/locale.conf`
  * Put **LANG=en_US.UTF-8**
* `vim /etc/vconsole.conf`
  * Put **KEYMAP=fr-latin1**
* `vim /etc/hostname`
  * Put hostname
* `vim /etc/hosts`
  * 127.0.0.1     localhost
  * ::1           localhost
  * 127.0.0.1     hostname
* `exit`
* `umount -R /mnt`
* `reboot`
* `login using root creds`
* `pacman -S open-vm-tools` (If VM)
* `pacman -S neofetch` (Very important)
