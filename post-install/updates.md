---
description: 'TODO: guide for macOS point updates and updates to OpenCore, kexts etc.'
---

# OS Updates & Maintenance

### Additional Tools

* Xcode \(required for OCBuilder, OC-Tool also for plist editor\)
* OCBuilder \([Support thread](https://www.insanelymac.com/forum/topic/339346-opencore-build-app/)\)
* [OC-Tool](https://github.com/rusty-bits/OC-tool) for maintenance
* PlistEdit Pro \(very nice commercial plist editor\)
* DiffMerge, to check how sample.plist has changed 

### Alternate workflow using OCBuilder to compile most recent OC

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

