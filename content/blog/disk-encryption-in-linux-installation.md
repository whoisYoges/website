+++
title = "Disk encryption in linux installation"
date = "2022-12-22"
page_template = "page.html"
description = "Disk encryption in linux prevents a disk drive, like a hard drive or a portable USB storage device or laptop, from booting up unless the user inputs the correct authentication data. And here we're going to encrypt a disk while installing linux and learn how it works?"
[extra]
opengraph = "/assets/images/blogs/disk-encryption-in-linux-installation/disk-encryption-in-linux-installation.jpg"
shareable = true
keywords = "Encrypt,Encryption key,Disk encryption software,Full disk encryption, File encryption, Hard drive encryption, BitLocker, VeraCrypt, Disk encryption algorithms, Data encryption, lvmonluks, luks encryption"
+++
Disk encryption in linux prevents a disk drive, like a hard drive or a portable USB storage device or laptop, from booting up unless the user inputs the correct authentication data. And here I'm going to talk about my preferred method of disk encryption while installing linux and see how it works?
<!-- more -->

![disk-encryption-in-linux-installation](/assets/images/blogs/disk-encryption-in-linux-installation/disk-encryption-in-linux-installation.jpg)

## Introduction

The booting up process for an operating system involves the first section of the disk — the master boot record — informing the system of where to read the first file, which initiates the loading of the operating system. Without encryption, no special instructions are required to interpret the contents of the disk. By default, files are written in plain text.

When you use disk encryption, this process is modified. The contents of the disk (except for the master boot record) are encrypted using a modern symmetric cipher accessible via a secret key. The master boot record is modified so that it loads this system, which validates the authentication data from the user. If the authentication process is successful, the encryption key is unlocked.

This system, which varies between different implementations, stores the master key for the device. Authentication information might be a password, a public key-based token, or a fingerprint scan. Once the valid authentication data is read, the master key is decrypted. The master key then remains in the computer’s memory while it’s powered-on. This allows the operating system to first read the disk to boot up, as well as read any other disk contents the user requests while using the computer.

## Who Uses Disk Encryption

The main motive of encryption is to keep your data and personal information safe from others. So If anyone other than you has any access to your computer, then in should be encrypted. Also, I highly recommend encrypting the portable devices like laptops and raspberry-pi that has a chance of getting lost, stolen or access by others.

## My preferred method of disk encryption

So I do have a sigle hard drive in my computer so, I use [LVM](https://wiki.archlinux.org/title/LVM) on [LUKS](https://wiki.archlinux.org/title/Dm-crypt) encrypting all the filesystem and partitions excluding /boot partiton of grub bootloader. If you have multiple hard drives you may want to setup [RAID](https://wiki.archlinux.org/title/RAID) I guess. Checkout [arch wiki](https://wiki.archlinux.org/title/dm-crypt/Encrypting_an_entire_system) for more details about encryption types.

### How to Set-up LVM on LUKS

Okay Let's directly talk about how we can setup my preferred encryption type for single storage device computers.

1. Partition your storage into two using [GPT](https://wiki.archlinux.org/title/Partitioning#GUID_Partition_Table); First one is the boot partition of about 500MB and remaining the second.

2. Let's say **/dev/sda2** is the second partition, then setup LUKS in **/dev/sda2**.  
    a. `cryptsetup luksFormat /dev/sda2`  
    b. `cryptsetup open /dev/sda1 cryptlvm`  
    It can be mapped to any name in place of `cryptlvm`.  
    The decrypted container is now available at /dev/mapper/cryptlvm

3. Prepare the logical volumes
    a. Create a physical volume on top of the opened LUKS container:  
    `pvcreate /dev/mapper/cryptlvm`  
    b. Create a volume group (in this example named `groot`, but it can be whatever you want) and add the previously created physical volume to it:   
    `vgcreate groot /dev/mapper/cryptlvm`  
    c. Create all your logical volumes for root, home, swap and others as per your requirements on the volume group:  
    `lvcreate -L 8G groot -n swap`  
    `lvcreate -L 100G groot -n root`  
    `lvcreate -l 100%FREE groot -n home`

4. Format your file systems  
    `mkfs.ext4 /dev/groot/root`  
    `mkfs.ext4 /dev/groot/home`  
    `mkswap /dev/groot/swap`  
    `mkfs.fat -F 32 /dev/sda1` (for your bootloader(boot partition))

5. Mount your filesystems:  
    `mount /dev/groot/root /mnt`  
    `mount --mkdir /dev/groot/home /mnt/home`  
    `swapon /dev/groot/swap`  
    `mount --mkdir /dev/sdb1 /mnt/boot`

6. Now install the OS as you do normally and chroot into the newly installed system.

7. Configuring mkinitcpio:  
    a. Make sure you have installed [cryptsetup](https://archlinux.org/packages/core/x86_64/cryptsetup/) and [lvm2](https://archlinux.org/packages/core/x86_64/lvm2/).  
    b. Add the `keyboard`, `keymap`, `encrypt` and `lvm2` hooks to /etc/mkinitcpio.conf  
    `HOOKS=(base udev autodetect modconf kms keyboard keymap consolefont block encrypt lvm2 filesystems fsck)`

8. Configuring the boot loader  
    a. Get the UUID of /dev/sda2 (your LUKS partition) using blkid command.  
    `# blkid`  
    The Output should seem like following:  
    `/dev/sda2: UUID="27da5fec-b1f2-4b54-b2af-a2832d2c4522" TYPE="crypto_LUKS" PARTUUID="eeef0000-db63-5749-90d4-55c978558643"`  
    b. Set the kernel parameter in boot loader (grub) in /etc/default/grub  
    `cryptdevice=UUID=Your-UUID:cryptlvm root=/dev/groot/root`  
    It should seem like following:  
    `GRUB_CMDLINE_LINUX="cryptdevice=UUID=27da5fec-b1f2-4b54-b2af-a2832d2c4522:cryptlvm root=/dev/groot/root"`

9. Regenerate the initramfs  
    `mkinitcpio -P`

10. Regenerate grub config  
    `grub-mkconfig -o /boot/grub/grub.cfg`
