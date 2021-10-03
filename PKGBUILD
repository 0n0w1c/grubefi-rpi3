pkgname=grubefi-rpi3
pkgver=1.3
pkgrel=2
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
         '944db3a429918e88428bde8b658fb681'
         'e8154e17fd44ee949cd1d2a506b161ab'
         '780f27cc63514018f4fc373dbba91b3f'
         '9b4afbca83c63b826416187809cb3d1e'
         '027254ce97c7b50485a5854b989ec876'
         '9b4afbca83c63b826416187809cb3d1e')

package() {
   install -D bcm2710-rpi-3-b.dtb $pkgdir/boot/efi/bcm2710-rpi-3-b.dtb
   install -D bcm2710-rpi-3-b-plus.dtb $pkgdir/boot/efi/bcm2710-rpi-3-b-plus.dtb
   install -D bcm2710-rpi-cm3.dtb $pkgdir/boot/efi/bcm2710-rpi-cm3.dtb
   #install -D overlays/* $pkgdir/boot/efi/overlays
   install -d $pkgdir/boot/efi/firmware
   install -D firmware/* $pkgdir/boot/efi/firmware
   install -D bootcode.bin $pkgdir/boot/efi/bootcode.bin
   install -D start.elf $pkgdir/boot/efi/start.elf
   install -D fixup.dat $pkgdir/boot/efi/fixup.dat
   install -D Readme.md $pkgdir/boot/efi/Readme.md
   install -D RPI_EFI.fd $pkgdir/boot/efi/RPI_EFI.fd
   install -D config.txt $pkgdir/boot/efi/config.txt.uefi

   install -Dm 644 watch-cmdline.path $pkgdir/etc/systemd/system/watch-cmdline.path
   install -Dm 644 watch-cmdline.service $pkgdir/etc/systemd/system/watch-cmdline.service
   install -Dm 644 watch-config.path $pkgdir/etc/systemd/system/watch-config.path
   install -Dm 644 watch-config.service $pkgdir/etc/systemd/system/watch-config.service

   install -Dm 644 95-update-grubefi.hook $pkgdir/usr/share/libalpm/hooks/95-update-grubefi.hook

   install -Dm 755 update-grubefi $pkgdir/usr/bin/update-grubefi
}
