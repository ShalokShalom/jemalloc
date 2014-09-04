pkgname=jemalloc
pkgver=3.6.0
pkgrel=1
pkgdesc="General-purpose scalable concurrent malloc implementation"
arch=('x86_64')
license=('BSD')
url="http://www.canonware.com/jemalloc/"
depends=('glibc')
makedepends=('autoconf' 'make' 'bash')
optdepends=(
	'perl: memory profiler'
)
source=(http://www.canonware.com/download/jemalloc/$pkgname-$pkgver.tar.bz2)

build() {
	cd "$srcdir/$pkgname-$pkgver"
	CFLAGS="$CFLAGS -std=gnu11" ./configure --prefix=/usr
	make
}

package() {
	cd "$srcdir/$pkgname-$pkgver"
	make DESTDIR="$pkgdir" install
	mv "$pkgdir"/usr/bin/{,jemalloc-}pprof
	chmod 644 "$pkgdir"/usr/lib/*.a
	install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
}

sha256sums=('e16c2159dd3c81ca2dc3b5c9ef0d43e1f2f45b04548f42db12e7c12d7bdf84fe')
