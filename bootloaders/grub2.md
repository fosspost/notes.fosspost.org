# GRUB2

## [Problem] Other Distributions Can't Detect openSUSE/SUSE In The Bootloader

### Description

If you had openSUSE/SUSE installed on one of your hard disk partitions. And then you installed another Linux distribution on another partition and assigined the bootloader managment to the new distribution. You may notice that openSUSE/SUSE won't show in the boot menu anymore.

Even when you try to update GRUB or recreate its configuration file, it may tell you in the terminal output that it detects it, but you never see it in the boot menu.

This is because openSUSE/SUSE is using a special GRUB version which is patched downstream to be able to work with Btrfs setup and subvolumes. If you are using such setup, then you may face the same problem.

### Solution

You must make openSUSE/SUSE control the GRUB bootloader. To do this, run the following commands after your replace **/dev/sda1** with the openSUSE/SUSE partition you have:

    mount /dev/sda1 /mnt
    mount --bind /dev /mnt/dev
    mount --bind /proc /mnt/proc
    mount --bind /sys /mnt/sys
    chroot /mnt
    grub2-install /dev/sda

Then you can make a reboot. Later on you can update GRUB from inside openSUSE in order to detect the other operating systems you have on disk.
