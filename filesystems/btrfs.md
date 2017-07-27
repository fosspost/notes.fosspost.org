# Btrfs

## [Note] Df Command Doesn't Show Enough Output About Btrfs Filesystems

### Description

If you use **df** with options like **-i**, you may see empty output or not enough information about the disks.

### Solution

Use **btrfs** command and its utilities to manipulate Btrfs partitions:

    sudo btrfs filesystem df /

## [Problem] Programs Suddenly Stop Working/Crash

### Description

Sometimes, you may encounter different problems on distributions running on Btrfs filesystem because of "no disk space" error. Although you may have some free disk space, you would notice that a lot of applications and programs are suddenly crashing.

Firefox, Steam, Zypper, Chromium and a lot of other apps may just stop working suddenly with errors like:

    Cannot write file '/var/adm/mount/AP_0xBl0ihT/repodata/repomd.xml'.

    WARNING: Unix error 28 during operation move on file /myuser/.mozilla/firefox/xofrqlc6.default/saved-telemetry-pings/xxxxxxxx-bbd4-468a-a034-19111020d2ce.tmp (No space left on device)
    
This is because of a strange bug with some Btrfs installations. The system doesn't recognize that it has free space to use. Which makes software crash instantly when there's not enough space for them.

### Solution

As a workaround, you may remove some big files/data from your hard disk in order to get everything to work again.

## [Problem] Btrfs Doesn't Support Swap File

### Description

This is a known problem with Btrfs. Unfortunately, it doesn't have a solution. You'll need to create a separated swap partition in order to use it with a Btrfs filesystem.
