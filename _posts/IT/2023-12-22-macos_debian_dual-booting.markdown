---
layout: post
title:  "MacOS and Linux Debian 12 Bookwarm dual booting!"
date:   2023-12-22 13:04:22 +0100
last_modified_at: "{{ site.time | 2023-12-22T14:10:00+01:00 }}"
categories: data-science 
tags: [MacOS, Debian]
---

# Why Dual-Boot
- New MacOS and applications don't support old MacBooks, which are still functioning well.
- Old MacBook runs Linux OS much faster than MacOS, shutting down in seconds.
- We can use an old MacBook to try Linux distros, suitable for presentation and coding.

I chose the Debian 12 Bookworm distro. 

# Set dual-booting
Follow the instructions [Dual boot - Mac OS X & Debian]
[Dual-boot-Debian], we can easily set up the dual-booting.

## Preparations
- Back up all data.

In case of installing Debian failed, the MacOS can't be booted. `⌘+R`/Disk Utility, can't delete the last Linux partition, after some data has been written into the `swap` partition, the Debian installation disk can't recognize it and use that partition for `swap` again, so you need to erase the whole disk and partition again.   

- 2 USB disks, >= 16GB

1. Making a **MacOS** bootable USB. In case the MacOS can't be restored, and the _Apple Internet Recovery_ could be failed in the last a few minutes.
1. Making a **Debian-12** bootable USB. Just the internet installer is OK, even though making a full distro USB (~3.9GB), you still need to connect to the internet to complete the installation.
1. Ethernet cable, if there is a port on the laptop, then need a USB-ethernet adaptor.
1. Non-bluetooth mouse. During one step of installing Genome software, you need a mouse to click `continue`, otherwise, you can't move on. 

## Install Debian-12
[rEFInd][rEFInd] boot manager is not necessary, it needs to go to safe mode with`⌘+R` for two times, Debian installer will install **GRUB** boot manager in the final step.

When booting, pressing `Option` to select MacOS, the default is **Debian**, even installing MacOS after Debian, if MacOS needs to be reinstalled.

## Install network driver

MacBooks normally use **Broadcom** WiFi adaptor, the wireless driver can be downloaded from [Broadcom][Broadcom] with the following commands:

{% highlight bash %}
# need to install aptitude package manager
sudo apt install aptitude
sudo aptitude install dkms
sudo dpkg -i broadcom-sta-dkms_xxx_all.deb
{% endhighlight %}

With the above steps, it should be successful.:sparkles::congratulations:. 


[Dual-boot-Debian]: https://wiki.debian.org/MacBook
[Debian-12]: https://www.debian.org/News/2023/20230610
[rEFInd]: https://sourceforge.net/projects/refind/
[Broadcom]: https://packages.debian.org/bookworm/all/broadcom-sta-dkms/download
