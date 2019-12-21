---
description: >-
  from the Hackintool Help Page (not yet modified) - TODO: change to make it
  more applicable to OpenCore
---

# USB Port Patching

macOS 10.14.1+ does not work with the USB port limit patch and therefore there is no way to have all ports available to configure at one time. RehabMan has updated USBInjectAll.kext to include boot flags for excluding groups of ports

1. Place the [USBInjectAll.kext](https://bitbucket.org/RehabMan/os-x-usb-inject-all/downloads/) \(for port discovery\) into EFI/CLOVER/kexts/Other
2. USBInjectAll.kext Requirements:
3. Clover-&gt;DSDT Renames \(if detected\)
   * XHCI -&gt; XHC
   * XHC1 -&gt; XHC
   * EHC1 -&gt; EH01
   * EHC2 -&gt; EH02
4.  Reboot
5.  Run Hackintool then go to General-&gt;Installed to check USBInjectAll is installed correctly
   * Eg. USBInjectAll: Yes \(Release-0.7.1\)
6.  Go to the General-&gt;USB tab to check your USB Controllers list. Based on your USB Controller you may need to install additional kexts:
   * 8086:8CB1 and macOS &lt; 10.11.1 -&gt; XHCI-9-series.kext
   * 8086:8D31, 8086:A2AF, 8086:A36D, 8086:9DED -&gt; XHCI-unsupported.kext
   * 8086:1E31, 8086:8C31, 8086:8CB1, 8086:8D31, 8086:9C31, 8086:9CB1 -&gt; FakePCIID.kext + FakePCIID\_XHCIMux.kext
7.  Reboot if you need to install one of the additional kexts then run Hackintool again
8.  Go to the General-&gt;USB tab
9.  Select all items in the USB Ports list and select the “Delete” then the “Refresh” button
10.  Reboot with -uia\_exclude\_ss uia\_include=HS01,HS02 boot flags
    * Change the HS01,HS02 ports to the ones you have your mouse and keyboard attached
11.  Run Hackintool and go to the General-&gt;USB tab
12. Plug and unplug a USB 2.0 device into all ports on your system
    * The ports that are active will remain highlighted green
    *  Delete all ports that are not highlighted green
13.  Reboot with -uia\_exclude\_hs boot flag and remove the -uia\_exclude\_ss boot flag
14.  Run Hackintool and go to the General-&gt;USB tab
    * Plug and unplug a USB 3.0 device into all ports on your system
    * Plug and unplug a TypeC device into all ports \(in both orientations\)
    * The ports that are active will remain highlighted green
    *  Delete all ports that are not highlighted green
15.  Set each port to the appropriate Connector using the drop down list
    * USB ports with devices permanently attached \(eg. M.2 Bluetooth card\) should be set to “Internal”
    * HSxx ports connected to USB3 ports should be set to USB3
    * Internal HUBs are typically connected to ports PR11 and PR21 and therefore should be set to “Internal”
    * TypeC:
      * If it uses the same HSxx/SSxx in both orientations, then it has an internal switch \(use “TypeC+Sw”\)
      * If it uses a different HSxx/SSxx in each orientation, then it has no switch \(use “TypeC”\)
16. Use the “Export” button to generate files to your Desktop
    * Copy SSDT-EC.aml \(if created\) to EFI/CLOVER/ACPI/patched
    * Choose one of the following two:
      1. Copy USBPorts.kext to EFI/CLOVER/kexts/Other or;
      2. Copy SSDT-UIAC.aml and SSDT-USBX.aml \(if created\) to EFI/CLOVER/ACPI/patched
17. You can now perform a clean up and remove unnecessary files:
    * Remove custom boot flags \(-uia\_exclude\_ss -uia\_exclude\_hs uia\_include=x\)
    * Remove USBInjectAll.kext \(if using USBPorts.kext\)
18. Reboot
19. Run Hackintool and go to the General-&gt;USB tab
20. Select all items in the USB Ports list and select the “Delete” then the “Refresh” button
    * Now you can check all ports are working correctly
    * If you need to change a Connector type you will need to export your USBPorts.kext over the current one
    * If you made a mistake delete USBPorts.kext and start from the beginning of the instructions again

Q. What is USBPorts.kext?  
A. It's a [Codeless Kernel Extension](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KEXTConcept/KEXTConceptAnatomy/kext_anatomy.html) used to inject the USB ports

Q. Do I need SSDT-UIAC.aml?  
A. No, this method uses a codeless kext

