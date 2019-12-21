---
description: Under Construction (this is just a work in progress)
---

# Introduction & TODO

### Why this guide

I would like to create a beginner friendly OpenCore guide which uses mainly GUI Tools to create a vanilla hackintosh install. This should make OpenCore as accessible and and almost as easy to use as doing a vanilla Clover install. Everything done by these tools is transparent to the user and allows complete customisation. All downloads are from official sources, usually from the Github repos of the original developers.

### Who this guide is for

* those who are fairly new to hackintoshing \(preferably have at least some prior hackintosh experience\)
* those who are new to OpenCore, who would like a quickstart to get into OpenCore
* those who would like to try a new beginner friendly workflow which might help to get friends or family to learn how to hackintosh

### Hardware Prerequisites

* an existing computer running macOS \(High Sierra, Mojave or Catalina\)
* recent beginner friendly hardware
  * Intel CPU \(Kaby Lake or Coffee Lake\)
  * preferably Gigabyte or ASUS Mobo
  * 8 GB or more RAM 
  * NVMe or Sata SSD as main drive
  * AMD GPU or use iGPU
  * compatible Wifi & Bluetooth

### Overview

On a computer with macOS and Xcode follow these steps

1. Download and run [OCBuilder](https://github.com/Pavo-IM/ocbuilder/releases)
2. OCBuilder will build OpenCore incl. kexts  \(check OC version\)
3. [Download Open Core Configurator](https://mackie100projects.altervista.org/download-opencore-configurator/) \(check OCC version compatibility\)
4. Copy sample.plist to /EFI/OC/ folder and rename to config.plist
5. Edit config.plist in Open Core Configurator \(following the guide\)
6. Download [TINU](https://github.com/Pavo-IM/ocbuilder/releases) \([3.0 Beta 2](https://mega.nz/#!D0IgVa6R!Bdl5yY5p6GBilWxqTly7RbEACSIKobrF9m-SvmIBL8M)\)
7. Download macOS using TINU \(via App Store\)
8. Create USB using TINU \(which adds macOS and the OC EFI folder\)
9. Boot from USB stick and install macOS 
10. Mount EFI Partition using TINU
11. copy EFI folder to EFI partition on main disk
12. Reboot from main disk
13. On new macOS Download [Hackintool](http://headsoft.com.au/download/mac/Hackintool.zip)

### Software to download and Tools to be used

* Xcode \(for OCBuilder and plist editor\)
* TINU 3.0 Beta 2 or above
  * macOS Mojave 10.14.6+ or Catalina 10.15.2+
* Hackintool 2.8.8 or above
* OpenCore 0.5.3 or above
* Open Core Configurator 1.10.2 or above
* OCBuilder \([Support thread](https://www.insanelymac.com/forum/topic/339346-opencore-build-app/)\)
* optional [OC-Tool](https://github.com/rusty-bits/OC-tool) for maintenance

