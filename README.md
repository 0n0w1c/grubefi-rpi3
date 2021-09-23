# grubefi-rpi3
![grub2](https://user-images.githubusercontent.com/47831850/134357018-3530c95c-e774-45e7-af97-f830882b6a62.jpg)
#### Grubefi your Pi ####

An experimental PKGBUILD for Manjaro ARM RPi3 B+ installations. \
It will convert a RPi3 B+ from booting via firmware to UEFI and grub. \
And when removed, it will revert to firmware. \
You can install and remove at will, with or without rebooting.
 
Minimal change to how a Manjaro ARM RPi3 installation is maintained. \
The exception is the addition of the `update-grubefi` command, \
which can be used to manually update boot configuration changes to UEFI. \
In most situations, the boot configuration will update automatically. \
The boot configuration being config.txt, cmdline.txt, and overlays.

- - - -
#### Installation ####

1) A fresh installation is recommended, updated to arm-testing
 
2) sudo pacman -S linux-rpi4-mainline linux-rpi4-mainline-headers
 
3) Download the PKGBUILD or `git clone https://github.com/0n0w1c/grubefi-rpi3.git`
 
4) makepkg -sic

- - - -
#### Release Notes ####
Raspberry Pi 3 UEFI Firmware version 1.36 \
For more information, refer to the [README.md](https://github.com/pftf/RPi3/blob/master/Readme.md "RPi3 UEFI").

The headphone jack is enabled, to better mimic booting via the RPi3 firmware.

grub-mkconfig will run each time update-grubefi is executed.

It is a bit slow to boot with an SD card, be patient.

The fat32 partition, mounted as /boot/efi is considered the UEFI sandbox. \
Do not store your files in this location. All files in /boot/efi/ will be deleted \
upon removal of the this package with `pacman -R grubefi-rpi3`.

Warning: DO NOT have a shell (terminal) or files, open in /boot or /boot/efi during \
the installation or removal processes.

#### Warning: This is EXPERIMENTAL software, total data loss is a real possibility. ####
