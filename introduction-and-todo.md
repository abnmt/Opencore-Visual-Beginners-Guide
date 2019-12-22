---
description: 'Under Construction (this is just a work in progress) [inline TODO]'
---

# Introduction

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

On a computer with macOS follow these steps

* Download [TINU](https://github.com/ITzTravelInTime/TINU/releases) \(or TINU [3.0 Beta 2](https://mega.nz/#!D0IgVa6R!Bdl5yY5p6GBilWxqTly7RbEACSIKobrF9m-SvmIBL8M)\) and run
* Download macOS using TINU via App Store \(or using [Dosdude macOS Patcher](http://dosdude1.com/software.html) \)
* Create USB using TINU \(which formats USB stick and adds macOS\)
* Return to TINU Main Menu and _Mount EFI Partition_ \(Open in Finder\)
* Download the following tools to the USB stick \(on _Install macOS ..._ partition\)
  * [Hackintool](http://headsoft.com.au/download/mac/Hackintool.zip)
  * [MaciASL](https://github.com/acidanthera/MaciASL/releases) 
  * [Open Core Configurator](https://mackie100projects.altervista.org/download-opencore-configurator/) \(OCC\) 
* Run OCC to download OpenCore drivers and kexts to the USB EFI Partition
  * Tools - Open Core Downloader - select Location: EFI
  * Tools - Install Drivers - target partition: EFI
  * Tools - Kexts Installer - target partition: EFI
* Copy sample.plist from Docs to EFI/OC folder and rename to config.plist
* Edit config.plist in Open Core Configurator \(see below\)
* Boot from USB stick and install macOS 
* Reboot from main disk
* On new macOS use Hackintool for USB mapping

#### Edit config.plist in Open Core Configurator

\[add screenshots, and details for each CPU platform\] 

Hover over each option with the mouse which will show explanation from _Configuration.pdf._ For easier reading also Open Docs/Configuration.pdf next to OCC 

* ACPI \[ find the easiest way to add [SSDT-EC-USBX](https://github.com/acidanthera/OpenCorePkg/blob/master/Docs/AcpiSamples/SSDT-EC-USBX.dsl) ? \]
* Device Properties \[ find the simplest way to determine _`ig-platform-id`_ \]
* Kernel
  * Add kexts \(Browse - multiple select, it will ignore duplicates\)
    * then disable unused kexts
* Misc
  * Boot
    * PollAppleHotkeys \(check\)
* NVRAM
  * 7C436110-AB2A-4BBB-A880-FE41995C9F82
    * nvda\_drv \(blank\)
    * prev-lang:kbd \(blank, because the default gets you Russian\)
  * boot-args `-v keepsyms=1 dart=0 debug=0x100`
* PlatformInfo
  * SMBIOS
    * Model Selector `iMac14,2` \(on the bottom right, next to Check Coverage\)
    * uncheck\(!\) _Add this section_ \(the info has been copied to Generic which is all we need\)
  * Datahub - Generic - PlatformNVRAM
    * Generic
      * UUID [https://www.uuidgenerator.net/](https://www.uuidgenerator.net/) 
    * PlatformNVRAM
      * Automatic \(check\)
* UEFI
  * Add drivers \(Browse - multiple select, it will ignore duplicates\)
    * remove unused driver

### Alternate using OCBuilder to compile most recent OC

On a computer with macOS and Xcode follow these steps

* Using Disk Utility - View - Show All Devices
  *  format a 8GB+ USB stick _Mac OS Extended \(Journaled\)_ with _GUID Partition Map_ 
* Mount EFI from USB stick \(only mount the USB EFI partition\)
* Download and run [OCBuilder](https://github.com/Pavo-IM/ocbuilder/releases)
* OCBuilder will build OpenCore incl. kexts  \(check OC version\)
* [Download Open Core Configurator](https://mackie100projects.altervista.org/download-opencore-configurator/) \(check OCC version compatibility\)
* Copy sample.plist to /EFI/OC/ folder and rename to config.plist
* Edit config.plist in Open Core Configurator \(following the guide\)
* Download [TINU](https://github.com/Pavo-IM/ocbuilder/releases) \([3.0 Beta 2](https://mega.nz/#!D0IgVa6R!Bdl5yY5p6GBilWxqTly7RbEACSIKobrF9m-SvmIBL8M)\)
* Download macOS using TINU \(via App Store\)
* Create USB using TINU \(which adds macOS and the OC EFI folder\)
* Boot from USB stick and install macOS 
* Mount EFI Partition using TINU
* copy EFI folder to EFI partition on main disk
* Reboot from main disk
* On new macOS Download [Hackintool](http://headsoft.com.au/download/mac/Hackintool.zip)

### Software to download and Tools to be used

* * TINU 3.0 Beta 2 or above
  * macOS Mojave 10.14.6+ or Catalina 10.15.2+
* Hackintool 2.8.8 or above
* OpenCore 0.5.3 or above
* Open Core Configurator 1.10.2 or above
* MaciASL 1.5.6 or above from [https://github.com/acidanthera/MaciASL/releases](https://github.com/acidanthera/MaciASL/releases)
* possibly OCBuilder \([Support thread](https://www.insanelymac.com/forum/topic/339346-opencore-build-app/)\)
* Xcode \(required for OCBuilder also for plist editor\)
* optional [OC-Tool](https://github.com/rusty-bits/OC-tool) for maintenance
* optional PlistEdit Pro
* 
