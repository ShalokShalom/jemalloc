pkgname=jemalloc
pkgver=5.2.0
pkgrel=1
pkgdesc="General-purpose scalable concurrent malloc implementation"
arch=('x86_64')
license=('BSD')
url="http://www.canonware.com/jemalloc/"
depends=('glibc' 'gcc-libs')
makedepends=('autoconf' 'make' 'bash')
source=("https://github.com/jemalloc/jemalloc/releases/download/${pkgver}/${pkgname}-${pkgver}.tar.bz2")
sha256sums=('74be9f44a60d2a99398e706baa921e4efde82bf8fd16e5c0643c375c5851e3b4')


build() {
	cd "$srcdir/$pkgname-$pkgver"
	CFLAGS="$CFLAGS -std=gnu11" ./configure --prefix=/usr
	make
}

package() {
	cd "$srcdir/$pkgname-$pkgver"
	make DESTDIR="$pkgdir" install
	chmod 644 "$pkgdir"/usr/lib/*.a
	install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
}

