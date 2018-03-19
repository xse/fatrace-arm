# fatrace aur package with armv6h patch
# Maintainer: xse <183953+xse@users.noreply.github.com>
pkgname=fatrace
pkgver=0.12
pkgrel=1
pkgdesc="Reports file access events from all running processes, patched for armv6h"
arch=("armv6h" "armv7h")
url="http://launchpad.net/fatrace"
license=('GPL')
#depends=('python' 'powertop') # This stuff is optional if you only need fatrace, it's added for the py script, i'm not using it here.
source=("http://launchpad.net/fatrace/trunk/${pkgver}/+download/$pkgname-$pkgver.tar.bz2" "fatrace.patch")
sha256sums=("50e71706f2cad4efc37c23bd292a2d3aa53dd883506e910267b2eeb5b241f66b" "caa9c7dc0792ab10f61296e98151a020947dbac3cf009c2cb57f432c561a8409")

build() {
    cd "$srcdir/$pkgname-$pkgver"
    sed -i "s/usr\/local/usr/ ; s/sbin/bin/" Makefile
    patch fatrace.c<../fatrace.patch
    make
}

package() {
    cd "$srcdir/$pkgname-$pkgver"
    make DESTDIR="$pkgdir/" install
}
