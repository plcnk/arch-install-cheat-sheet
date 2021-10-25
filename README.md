# Notes on how to install Arch Linux

## Install System

* `loadkeys fr-latin1`
* Try to ping something
* `timedatectl set-ntp true`
* `cfdisk /dev/sdx`
    * Select DOS
    * Select New -> 512M -> Primary
    * Type B to make partition bootable
    * Select remaining space: New -> Primary
    * Select Write -> yes
    * Quit
* `mkfs.ext4 /dev/sdx1`
* `mkfs.ext4 /dev/sdx2`
* `mount /dev/sdx2 /mnt`
* `mkdir /mnt/boot`
* `mount /dev/sdx1 /mnt/boot`
* `pacstrap /mnt base base-devel linux linux-firmware vim`
* `genfstab -U /mnt >> /mnt/etc/fstab`
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
    * Search for locale, uncomment and save
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
* `pacman -S neofetch`

## Add Desktop Environment

* `useradd -m user -s /bin/bash`
* `passwd user`
* `EDITOR=vim visudo`
    * Defaults      editor=/usr/bin/vim
    * user          ALL=(ALL) ALL
* `pacman -S xorg plasma plasma-wayland-session kde-applications`
* `systemctl enable sddm.service`
* `reboot`
