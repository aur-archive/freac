# Maintainer: archtux <antonio dot arias99999 at gmail dot com>

pkgname=freac
_realpkgver=20141005
pkgver=cvs_${_realpkgver}
pkgrel=3
pkgdesc="Audio converter and CD ripper with support for various popular formats and encoders."
arch=('i686' 'x86_64')
url="http://www.freac.org/"
license=('GPL2')
depends=('alsa-lib' 'gtk3' 'libxmu')

if [ "${CARCH}" = 'x86_64' ]; then
srcmd5='388c64149f78f693dcc58c5e6b07447f'
cpu=-x64
elif  [ "${CARCH}" = 'i686' ]; then 
srcmd5='cc8165ef092d403890c058fa716321e7'
fi

source=(http://sourceforge.net/projects/bonkenc/files/snapshots/$_realpkgver/freac-$_realpkgver-linux$cpu.tar.gz
        freac
        freac.desktop
        freaccmd
        translator)
md5sums=($srcmd5
        '1cf482f5536fe8f4df15de6bea4ead95'
        'fe5a8d47bfe0cccbfd12666f9d61ec4f'
        '729fd253ec04ceca75d1e6600fcf7265'
        '9c7ee1f50408d998b07d5f784ff4d753')

package() {
   cd $srcdir

   # Data files
   mkdir -p $pkgdir/usr/share/freac
   cp -r freac-$_realpkgver/* $pkgdir/usr/share/freac
   chmod -R 755 $pkgdir/usr/share/freac
   
   # Delete source code
   rm -rf $pkgdir/usr/share/freac/source
  
   # Start files
   install -Dm755 freac $pkgdir/usr/bin/freac
   install -Dm755 freaccmd $pkgdir/usr/bin/freaccmd
   install -Dm755 translator $pkgdir/usr/bin/translator

   # Desktop icon
   install -Dm644 freac-$_realpkgver/icons/freac.png $pkgdir/usr/share/pixmaps/freac.png
   install -Dm644 freac.desktop $pkgdir/usr/share/applications/freac.desktop
}