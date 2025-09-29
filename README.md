# Medion-S17404-Hackintosh-OpenCore

**Specs of this laptop:**
* Intel Core i5-10210U Comet Lake
* Intel UHD Graphics 620
* 8 GB DDR4 RAM
* Intel AX201 Wifi/Bluetooth
* Realtek ALC235 Audio Controller

**Working**
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

**Instructions**
**NOTE: If you're performing an online install, you'll need a USB-to-Ethernet dongle since WiFi won't work until you've installed HeliPort**
1. Follow dortania guide https://dortania.github.io/OpenCore-Install-Guide/installer-guide/ for creating a bootable install media.
2. Build your EFI.zip using the GitHub Actions Workflow https://github.com/Niktendo/Medion-S17404-Hackintosh-OpenCore/actions/workflows/Build-OpenCore.yml.
   Don't forget to create a custom .serialdata file and upload it e.g. to gist.github.com
4. Boot into macOS Installer from USB, erase your desired drive and install macOS. 
5. Setup macOS after finishing the installation.
6. Download and install HeliPort from https://github.com/OpenIntelWireless/HeliPort/releases to get WiFi working
7. Profit!
8. Optional: Mount your EFI partition using https://github.com/corpnewt/MountEFI and modify your config.plist using https://github.com/corpnewt/ProperTree to set Misc -> Security -> SecureBootModel to Default.
9. Optional: Mount the EFI partition of your USB drive and copy the contents to the EFI partition of your Macintosh HD to make booting without an USB key possible.
