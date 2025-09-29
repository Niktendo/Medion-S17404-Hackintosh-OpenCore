# Medion-S17404-Hackintosh-OpenCore

### Specs of this laptop
* Intel Core i5-10210U Comet Lake
* Intel UHD Graphics 620
* 8 GB DDR4 RAM
* Intel AX201 Wifi/Bluetooth
* Realtek ALC235 Audio Controller

### Working
* Display
* Integrated Graphics
* Keyboard
* Trackpad
* WiFi
* Bluetooth
* Battery Readout
* Webcam
* Microphone
* Audio
* iMessage/Facetime/Handoff
* Audio combojack headphone port
* Sleep/wake
* Keyboard backlight

### Instructions
**NOTE: If you're performing an online install, you'll need a USB-to-Ethernet dongle since WiFi won't work until you've installed HeliPort**
1. Follow dortania guide https://dortania.github.io/OpenCore-Install-Guide/installer-guide/ for creating a bootable install media.
2. Build your EFI.zip using the GitHub Actions Workflow https://github.com/Niktendo/Medion-S17404-Hackintosh-OpenCore/actions/workflows/Build-OpenCore.yml and copy it to your USB drive.
   Don't forget to create a custom .serialdata file and upload it e.g. to gist.github.com.
4. Boot into macOS Installer from USB, erase your desired drive and install macOS. 
5. Setup macOS after finishing the installation.
6. Download and install HeliPort from https://github.com/OpenIntelWireless/HeliPort/releases to get WiFi working.
7. Profit!
8. Optional: Mount your EFI partition using https://github.com/# orpnewt/MountEFI and edit your config.plist using https://github.com/corpnewt/ProperTree to set Misc -> Security -> SecureBootModel to Default.
9. Optional: Mount the EFI partition of your USB drive and copy the contents to the EFI partition of your Macintosh HD to make booting without an USB key possible.

### Fixing audio on macOS Tahoe
**NOTE: In order to make the onboard audio controller working again, you'll need to permanently disable Apple Secure Boot and System Integrity Protection. This is not permament, so you'll have to repeat these step after every system update.**

Since Apple has removed AppleHDA in Tahoe the only way to get working onboard audio is to patch the filesystem via OpenCore Legacy Patcher Mod.
1. Mount your EFI partition and open your config.plist.
2. Change the following entries:
   Misc -> Security -> SecureBootModel to Disabled
   NVRAM -> Add -> 7C436110-AB2A-4BBB-A880-FE41995C9F82 -> csr-active-config to <03080000>
   NVRAM -> Add -> 7C436110-AB2A-4BBB-A880-FE41995C9F82 -> boot-args add amfi=0x80
4. Reboot and clear NVRAM.
5. Download and install the latest Release of OCLP-Mod from https://github.com/laobamac/OCLP-Mod/releases.
6. Open OCLP-Mod and choose the top-right option (Yes, it's chinese - i've used Google Translate on my phone.).
7. Choose the first option in the dialog and wait until it's done.
8. Reboot and check your audio devices in settings.
9. Optional, but recommended: Mount your EFI partition, edit your config.plist and delete amfi=0x80 from NVRAM -> Add -> 7C436110-AB2A-4BBB-A880-FE41995C9F82 -> boot-args. Reset your NVRAM afterwards.
