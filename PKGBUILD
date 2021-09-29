pkgname=grubefi-rpi3
pkgver=1.1
pkgrel=1
uefiver=1.35
pkgdesc="grubefi your pi (3b+)"
arch=('aarch64')
url="https://github.com/0n0w1c/grubefi-rpi3"
license=('MIT')
depends=('grub' 'grub-theme-vimix' 'manjaro-arm-wallpapers')
provides=('grubefi-rpi3')
conflicts=()
options=('!strip')
install=grubefi-rpi3.install

source=("https://github.com/pftf/RPi3/releases/download/v$uefiver/RPi3_UEFI_Firmware_v$uefiver.zip"
        "https://raw.githubusercontent.com/0n0w1c/$pkgname/master/95-update-grubefi.hook"
        "https://raw.githubusercontent.com/0n0w1c/$pkgname/master/update-grubefi"
        "https://raw.githubusercontent.com/0n0w1c/$pkgname/master/grubefi-rpi3.install"
        "https://raw.githubusercontent.com/0n0w1c/$pkgname/master/watch-cmdline.path"
        "https://raw.githubusercontent.com/0n0w1c/$pkgname/master/watch-cmdline.service"
        "https://raw.githubusercontent.com/0n0w1c/$pkgname/master/watch-config.path"
        "https://raw.githubusercontent.com/0n0w1c/$pkgname/master/watch-config.service")

md5sums=('11d66f288c2ca136efd4003735fa084c'
         'c1c91ada19e8517ff17b0413c4b3e0c1'
         'c8f8d31232e9900de8b3109faed85004'
         '632f20d07232266185fcbc83e6d4812c'
         '780f27cc63514018f4fc373dbba91b3f'
         '9b4afbca83c63b826416187809cb3d1e'
         '027254ce97c7b50485a5854b989ec876'
         '9b4afbca83c63b826416187809cb3d1e')

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
