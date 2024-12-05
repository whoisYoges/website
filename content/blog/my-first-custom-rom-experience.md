+++
title = "My first custom ROM experience!"
description = "I used LineageOS 20 as a daily driver for over 3 months on my old Redmi phone. Here's my experience with custom ROMs: better performance, smooth UI, privacy, and some challenges to consider."
date = "2024-12-05"
page_template = "page.html"
draft = false
[extra]
opengraph = "/assets/images/blogs/custom-rom/lineageos.jpg"
gotoTop = true
shareable = true
viewallblogs = true
keywords = "custom rom, lineage os, castor, castorIsDead, castor is dead, zero to noob linux, whoisYoges, Yogesh Lamichhane, open source, FOSS, linux, geek, Arch, Artix, archlinux, arch linux, artix linux"
+++
I used LineageOS 20 as a daily driver for over 3 months on my old Redmi phone. Here's my experience with custom ROMs: better performance, smooth UI, privacy, and some challenges to consider.
<!-- more -->

After four years with my trusty Redmi phone, I decided to try something a little more adventurous: installing a custom ROM. I had previously switched the stock ROM to different regional MIUI versions (European and Indonesian) and was quite comfortable, but I had never ventured into the realm of custom ROMs. Enter **[LineageOS](https://lineageos.org)** 20 - an open-source, ad-free, and bloatware-free custom ROM that's known for its clean UI and privacy-first features. 

![Lineage OS](/assets/images/blogs/custom-rom/lineageos.jpg)

This blog is a technical dive into my experience, the steps I followed, and the lessons learned along the way. If you're on the fence about switching to a custom ROM like LineageOS, this might help you decide whether it's worth the effort. 

## The Basics: How I Installed LineageOS 20 on My Redmi Phone

I won’t go into an exhaustive step-by-step guide because installation can vary greatly depending on your device. However, here's a quick overview of what I did:

1. **Backup everything**: I made sure to back up all my important data on a computer.
2. **Unlock the bootloader**: This is necessary for installing a custom ROM. It's a bit tricky and requires permission from your device’s manufacturer (for Xiaomi, you need to use their unlock tool).
3. **Downgrade MIUI (Optional)**: My phone was running the latest MIUI version, which didn’t support custom recovery. I had to downgrade to a version that did, but this step might not be required for you.
4. **Install a custom recovery**: I flashed a custom recovery from the lineageos itself.
5. **Flash the ROM**: This involved flashing the LineageOS ROM and associated files (boot, vbmeta, dtbo, and super_empty images). Not all of these steps might be necessary, but they worked for me.
6. **Install LiteGApps**: Since I only needed Google Maps and the Play Store from google apps, I opted for the [litegapps](https://litegapps.github.io/) [SuperLite](https://litegapps.github.io/doc/litegapps_variant.html#superlite) version to minimize bloatware and google tracking.

If you're interested in custom ROMs, the **[XDA Developers](https://www.xda-developers.com/)** forum is a great place to start. It’s essentially a treasure trove of ROM guides and developer support.

## The Benefits I Experienced with LineageOS 20

Once everything was up and running, here are the key advantages I noticed immediately:

1. **A Clean, Super Smooth UI**: No bloatware, no adware—just a clean, fast UI. LineageOS was sleek, snappy, and felt like a breath of fresh air compared to the bloat-heavy stock MIUI experience.
2. **Nightly OTA Updates**: This was a game-changer. LineageOS offers regular nightly updates, ensuring my phone stays up-to-date with the latest security patches.
3. **Banking and Streaming Apps Work Out of the Box**: I was relieved to see that essential apps like Netflix, Google Pay, and various banking apps passed the integrity checks and worked without issues.
4. **Improved Privacy**: One of the key reasons I switched was to minimize tracking. LineageOS offers a higher level of privacy, giving me more control over app permissions.
5. **Longer Battery Life**: With bloatware out of the picture, I noticed improved battery life. It was a pleasant surprise, especially on a phone that was already several years old.
6. **More Storage**: With fewer pre-installed apps and system processes, I had more free space on my device.
7. **Self-Satisfaction**: There’s an undeniable feeling of accomplishment when you successfully install a custom ROM and enjoy a better experience on a device that’s been written off as obsolete.

## Challenges I Faced During the Switch

While the experience was largely positive, there were a few hurdles along the way:

1. **Bootloader Locking Issues**: One major frustration was that the bootloader could not be locked once I installed the custom ROM. Locking the bootloader requires manually compiling signed images and using a capable PC, which was beyond my setup. This also meant that Google Play’s integrity checks failed, so certain apps like **Indriver**, **Binance**, and **Banana Kong 2** wouldn’t install properly. I was able to sideload Indriver using the **[Aurora Store](https://auroraoss.com/)** APK, but other apps remained inaccessible.
2. **WiFi Connectivity**: LineageOS had some trouble connecting to hidden WiFi networks. It took anywhere from 10-20 seconds longer to discover and connect to them, which was a bit annoying at times.
3. **Missing Camera Features**: The default camera app from LineageOS was pretty basic. Missing features like panorama and timelapse were noticeable.

## Final Thoughts: Was It Worth It?

Despite the few challenges, my experience with LineageOS 20 was overwhelmingly positive. The performance boost, the ad-free environment, and the heightened privacy were all worth the effort. LineageOS delivered a noticeable improvement over MIUI, and the fact that my device was getting regular updates made it feel like I had a brand-new phone. 

Even though I have since moved on to a newer device, I still use my Redmi phone as a secondary device with LineageOS. I plan to continue experimenting with custom ROMs as long as my primary phone remains unsupported or outdated.

For those who are tech-savvy and willing to take on the occasional challenge, a custom ROM like LineageOS is definitely worth considering. It offers a level of control and performance that’s hard to match with stock ROMs.
