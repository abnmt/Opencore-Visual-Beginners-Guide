---
description: >-
  Under Construction (this is just a work in progress) - see inline [TODO] or
  ((TODO))
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
* Download macOS 
  * using TINU via App Store \(or using a [dosdude1 macOS Patcher](http://dosdude1.com/software.html) \)
* Create USB using TINU \(erases USB stick and adds macOS\)
* Return to TINU Main Menu and _Mount EFI Partition_ \(Open in Finder\)
* Download the following tools to the USB stick \(onto the _Install macOS ..._ partition\)
  * [Hackintool](http://headsoft.com.au/download/mac/Hackintool.zip)
  * [MaciASL](https://github.com/acidanthera/MaciASL/releases) \(Release\)
  * [Open Core Configurator](https://mackie100projects.altervista.org/download-opencore-configurator/) OCC \(System Preferences - Security - Open Anyway\)
* Run OCC to download OpenCore drivers and kexts to the USB EFI Partition. From the menu select: 
  * Tools - Open Core Downloader - Release - select Location: EFI
  * Tools - Install Drivers - target partition: EFI
  * Tools - Kexts Installer - target partition: EFI
* Copy sample.plist from Docs to EFI/OC folder and rename to config.plist \(\(add screenshot of EFI\)\)
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

### 

### Software to download and main Tools used

* * TINU 3.0 Beta 2 or above
  * macOS Mojave 10.14.6+ or Catalina 10.15.2+
* Hackintool 2.8.8 or above
* OpenCore 0.5.3 or above
* Open Core Configurator 1.10.2 or above
* MaciASL 1.5.6 or above from [https://github.com/acidanthera/MaciASL/releases](https://github.com/acidanthera/MaciASL/releases)
* * 
