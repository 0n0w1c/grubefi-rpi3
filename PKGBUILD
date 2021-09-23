pkgname=grubefi-rpi3
pkgver=1.0
pkgrel=0
uefiver=1.36
pkgdesc="grubefi your pi (3B+)"
arch=('aarch64')
url="https://github.com/0n0w1c/grubefi-rpi3"
license=('MIT')
depends=('grub' 'grub-theme-vimix' 'lsof' 'manjaro-arm-wallpapers')
provides=('grubefi-rpi3')
conflicts=()
options=('!strip')
install=grubefi-rpi3.install
source=("https://github.com/pftf/RPi3/releases/download/v$uefiver/RPi3_UEFI_Firmware_v$uefiver.zip"
        'https://github.com/0n0w1c/grubefi-rpi4/blob/master/95-update-grubefi.hook'
        'https://github.com/0n0w1c/grubefi-rpi4/blob/master/update-grubefi'
        'https://github.com/0n0w1c/grubefi-rpi4/blob/master/grubefi-rpi3.install'
        'https://github.com/0n0w1c/grubefi-rpi4/blob/master/watch-cmdline.path'
        'https://github.com/0n0w1c/grubefi-rpi4/blob/master/watch-cmdline.service'
        'https://github.com/0n0w1c/grubefi-rpi4/blob/master/watch-config.path'
        'https://github.com/0n0w1c/grubefi-rpi4/blob/master/watch-config.service')

md5sums=('c684b194a4d2e8b2ab597a3c09d0b2e8'
         'c1c91ada19e8517ff17b0413c4b3e0c1'
         '69ed8dde0c4211e5b8b0bec97ca0bf34'
         '67536bcd3845a99b5806c68b173fa757'
         '780f27cc63514018f4fc373dbba91b3f'
         'e3086a7d5c1dea1aeaed1674ccbbe176'
         '027254ce97c7b50485a5854b989ec876'
         'e3086a7d5c1dea1aeaed1674ccbbe176')

package() {
   mkdir -p $pkgdir/boot/efi
   mkdir -p $pkgdir/boot/overlays
   mkdir -p $pkgdir/etc/systemd/system
   mkdir -p $pkgdir/usr/share/libalpm/hooks
   mkdir -p $pkgdir/usr/bin

   cp bcm2710-rpi-3-b.dtb $pkgdir/boot/efi/
   cp bcm2710-rpi-3-b-plus.dtb $pkgdir/boot/efi/
   cp bcm2710-rpi-cm3.dtb $pkgdir/boot/efi/
   #cp -r overlays $pkgdir/boot/efi/
   cp -r firmware $pkgdir/boot/efi/
   cp bootcode.bin $pkgdir/boot/efi/
   cp start.elf $pkgdir/boot/efi/
   cp fixup.dat $pkgdir/boot/efi/
   cp Readme.md $pkgdir/boot/efi/
   cp RPI_EFI.fd $pkgdir/boot/efi/
   cp config.txt $pkgdir/boot/efi/config.txt.uefi

   cp watch-cmdline.path $pkgdir/etc/systemd/system/
   cp watch-cmdline.service $pkgdir/etc/systemd/system/
   cp watch-config.path $pkgdir/etc/systemd/system/
   cp watch-config.service $pkgdir/etc/systemd/system/

   cp 95-update-grubefi.hook $pkgdir/usr/share/libalpm/hooks/

   cp update-grubefi $pkgdir/usr/bin/
   chmod 755 $pkgdir/usr/bin/update-grubefi
}
