+++
title = "Disk encryption in linux installation"
date = "2022-12-22"
page_template = "page.html"
draft = true
description = "Disk encryption in linux prevents a disk drive, like a hard drive or a portable USB storage device or laptop, from booting up unless the user inputs the correct authentication data. And here we're going to encrypt a disk while installing linux and learn how it works?"
[extra]
opengraph = "/assets/images/blogs/disk-encryption-in-linux-installation/disk-encryption-in-linux-installation.jpg"
gotoTop = true
copy_code = true
shareable = true
commentable = true
keywords = ""
toc = "<p><a href='#introduction'>Introduction</a></p><p><a href='#who-uses-disk-encryption'>Who Uses Disk Encryption</a></p><h3>Also Read</h3><hr>"
+++
Disk encryption in linux prevents a disk drive, like a hard drive or a portable USB storage device or laptop, from booting up unless the user inputs the correct authentication data. And here I'm going to talk about my preferred method of disk encryption while installing linux and see how it works?
<!-- more -->

![disk-encryption-in-linux-installation](/assets/images/blogs/disk-encryption-in-linux-installation/disk-encryption-in-linux-installation.jpg)

<div class="blogcontents">

## Introduction

The booting up process for an operating system involves the first section of the disk — the master boot record — informing the system of where to read the first file, which initiates the loading of the operating system. Without encryption, no special instructions are required to interpret the contents of the disk. By default, files are written in plain text.

When you use disk encryption, this process is modified. The contents of the disk (except for the master boot record) are encrypted using a modern symmetric cipher accessible via a secret key. The master boot record is modified so that it loads this system, which validates the authentication data from the user. If the authentication process is successful, the encryption key is unlocked.

This system, which varies between different implementations, stores the master key for the device. Authentication information might be a password, a public key-based token, or a fingerprint scan. Once the valid authentication data is read, the master key is decrypted. The master key then remains in the computer’s memory while it’s powered-on. This allows the operating system to first read the disk to boot up, as well as read any other disk contents the user requests while using the computer.

## Who Uses Disk Encryption

The main motive of encryption is to keep your data and personal information safe from others. So If anyone other than you has any access to your computer, then in should be encrypted. Also, I highly recommend encrypting the portable devices like laptops and raspberry-pi that has a chance of getting lost, stolen or access by others.

</div>