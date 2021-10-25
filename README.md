# Notes on how to install Arch Linux

* `loadkeys fr-latin1`
* Try to ping something
* `timedatectl set-ntp true`
* cfdisk /dev/sdx
    * Select DOS
    * Select New -> 512M -> Primary
    * Type B to make partition bootable
    * Select remaining space: New -> Primary
    * Select Write -> yes
    * Quit
* mkfs.ext4 /dev/sdx1
* mkfs.ext4 /dev/sdx2
* mount /dev/sdx2 /mnt
* mkdir /mnt/boot
* mount /dev/sdx1 /mnt/boot
* pacstrap /mnt base base-devel linux linux-firmware vim
